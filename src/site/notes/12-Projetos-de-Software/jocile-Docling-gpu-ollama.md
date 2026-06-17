---
{"dg-publish":true,"permalink":"/12-projetos-de-software/jocile-docling-gpu-ollama/","metatags":{"description":"Processamento de documentos PDF com alta performance utilizando GPU para inferência VLM"},"tags":["Projeto","github","python","docling","gpu-acceleration"],"noteIcon":"1","updated":"2026-06-08T08:41:32.717-03:00","dg-note-properties":{"topics":["Script Python","Processamento de PDF"],"status":"active","visibility":"public","repository_url":"[Docling-gpu-ollama](https://github.com/jocile/Docling-gpu-ollama)","technologies":["Python","CUDA","Ollama","Docling"],"started":"2026-05-18","tags":["Projeto","github","python","docling","gpu-acceleration"]}}
---

# 📦 jocile/Docling-gpu-ollama

>[!summary] Script em Python desenvolvido para processar e converter documentos PDF utilizando a biblioteca [Docling](https://www.docling.ai/), com aceleração via GPU (CUDA) e integração ao ecossistema Ollama/VLM.

**Repositório**: [Docling-gpu-ollama](https://github.com/jocile/Docling-gpu-ollama)
**Tecnologias**: Python,CUDA,Ollama,Docling

## 🎯 Contexto

- **Objetivo Relacionado**: Processamento de documentos PDF com alta performance utilizando GPU para inferência VLM (Vision Language Model)
- **Deploy/Ambiente**: Local (Windows/Linux) via ambiente virtual Python (`venv`) com [PyTorch](https://pytorch.org/) CUDA 13.5

## ⚙️ DevOps & Manutenção

- [ ] Revisar alertas semanais do [Dependabot · GitHub](https://github.com/dependabot)
- [ ] Atualizar documentação baseada em [[23-Inteligencia-Artificial/Spec Driven Development\|Spec Driven Development]] (SDD)
- [ ] Revisar commits pendentes

## 📋 Tarefas (Backlog)

- [ ] Configurar ambiente local com suporte CUDA completo  
[priority:: high]
- [ ] Refatorar pipeline de conversão para melhor utilização da GPU  
[priority:: medium]
- [ ] Atualizar README.md com exemplos práticos e benchmarking  
[priority:: low]

## 🔧 Principais Scripts do Projeto

### `convertpdf.py`

Processamento principal de PDFs com:
- Aceleração por GPU (CUDA) via `AcceleratorDevice.CUDA`
- Processamento multithread (`ThreadedStandardPdfPipeline`)
- Batching otimizado: layout_batch_size=64, table_batch_size=4

### `converthtml.py`

Script simplificado para extração de dados diretamente de URLs HTML.

## 📖 Documentação Adicional

Referências completas sobre GPU acceleration com Docling estão disponíveis no repositório oficial:

- [Docling GPU Support](https://docling-project.github.io/docling/usage/gpu/)
- [Docling video tutorial](https://www.youtube.com/watch?v=IGDaXFmb1NU)
- [Docling RTX Getting Started](https://docling-project.github.io/docling/getting_started/rtx/)
