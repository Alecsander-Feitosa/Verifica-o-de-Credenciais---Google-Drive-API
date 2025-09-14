# 🔐 Verificação de Credenciais - Google Drive API

[![Python](https://img.shields.io/badge/Python-3.10+-blue.svg)](https://www.python.org/)
[![Google API](https://img.shields.io/badge/Google%20API-Drive-green)](https://developers.google.com/drive)
[![License](https://img.shields.io/badge/License-MIT-yellow.svg)](LICENSE)

Um script em **Python** que autentica com a **Google Drive API** usando uma **conta de serviço**  
e lista os primeiros arquivos encontrados na nuvem.  
Ideal para validar credenciais e testar integrações com o Google Cloud.  

---

## ✨ Funcionalidades
- ✅ Autentica com **Google Drive** via conta de serviço  
- 📂 Lista os primeiros arquivos da conta (padrão: 5 arquivos)  
- ⚡ Útil para verificar se as credenciais estão funcionando corretamente  
- 🛠️ Código limpo, estruturado e pronto para servir como **exemplo de portfólio**  

---

## 🖥️ Pré-requisitos
Antes de usar, você precisa de:
- Python **3.10+**
- Uma conta no [Google Cloud Console](https://console.cloud.google.com/)
- A **API do Google Drive** ativada no projeto
- Um arquivo de **credenciais JSON** da conta de serviço

---

## 📦 Instalação

1. Clone este repositório:
   ```
   git clone https://github.com/Alecsander-Feitosa/Verifica-o-de-Credenciais---Google-Drive-API

   
2. nstale as dependências:
 ```
pip install -r requirements.txt
```


▶️ Uso
Execute o script para verificar as credenciais:
```
python check.py
```

Se tudo estiver configurado corretamente, você verá algo como:

```
[INFO] Autenticação realizada com sucesso.

[INFO] Arquivos encontrados:
 - exemplo1.txt (ID: abc123)
 - exemplo2.pdf (ID: xyz789)
```


