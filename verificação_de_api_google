import os
import logging
from google.oauth2 import service_account
from googleapiclient.discovery import build
from googleapiclient.errors import HttpError


# Configuração do logger
logging.basicConfig(
    level=logging.INFO,
    format="%(asctime)s [%(levelname)s] %(message)s",
    datefmt="%d-%m-%Y %H:%M:%S"
)

# Constantes
CREDENTIALS_FILE: str = "CLS.json"
SCOPES: list[str] = ["https://www.googleapis.com/auth/drive.readonly"]


def authenticate(credentials_file: str = CREDENTIALS_FILE) -> "service_account.Credentials | None":
    """
    Autentica no Google Drive usando uma conta de serviço.
    
    :param credentials_file: Caminho para o arquivo JSON de credenciais.
    :return: Objeto de credenciais ou None em caso de erro.
    """
    if not os.path.exists(credentials_file):
        logging.error("Arquivo de credenciais '%s' não encontrado.", credentials_file)
        return None

    try:
        creds = service_account.Credentials.from_service_account_file(
            credentials_file, scopes=SCOPES
        )
        logging.info("Autenticação realizada com sucesso.")
        return creds
    except Exception as e:
        logging.error("Erro ao autenticar: %s", e)
        return None


def list_drive_files(creds, max_results: int = 5) -> None:
    """
    Lista os primeiros arquivos do Google Drive.
    
    :param creds: Credenciais autenticadas.
    :param max_results: Quantidade de arquivos a listar.
    """
    try:
        service = build("drive", "v3", credentials=creds)
        results = service.files().list(
            pageSize=max_results,
            fields="files(id, name)"
        ).execute()

        items = results.get("files", [])

        if not items:
            logging.warning("Nenhum arquivo encontrado no Google Drive.")
        else:
            logging.info("Arquivos encontrados:")
            for item in items:
                logging.info(" - %s (ID: %s)", item["name"], item["id"])

    except HttpError as error:
        logging.error("Erro de HTTP ao acessar a API: %s", error)
    except Exception as e:
        logging.error("Erro inesperado: %s", e)


def verify_credentials() -> None:
    """
    Executa o fluxo de verificação de credenciais.
    """
    logging.info("Iniciando verificação de credenciais...")
    creds = authenticate()
    if creds:
        list_drive_files(creds)
        logging.info("Verificação concluída com sucesso.")
    else:
        logging.error("Não foi possível autenticar. Verifique o arquivo de credenciais.")


if __name__ == "__main__":
    verify_credentials()
