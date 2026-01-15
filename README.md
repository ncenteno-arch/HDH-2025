# **Corrección del “tú” impersonal con Mistral-7B-Instruct**

Este proyecto usa Mistral-7B-Instruct con bitsandbytes (cuantización 4-bit) para:
- Corregir enunciados escritos en segunda persona (“tú”) en contextos generales, transformándolos en formas impersonales con “se”.
- Generar feedback que explica el tipo de error y su ajuste más adecuado.


### **Requisitos:**
- Python 3, torch, transformers, bitsandbytes, pandas, nltk, openpyxl.
- Autenticación en Hugging Face y acceso al modelo 'mistralai/Mistral-7B-Instruct-v0.3'.


### **Dataset:**
El dataset utilizado se ha subido al repositorio e-CienciaDatos:  
🔗 https://edatos.consorciomadrono.es/dataset.xhtml?persistentId=doi:10.21950/VVAJM1  
Contiene pares de oraciones: frase original con “tú” y su corrección impersonal con “se”.


### **Flujo básico:**
1. Carga y limpieza del dataset.
2. Generación de correcciones con Mistral-7B-Instruct.
3. Evaluación de calidad con GLEU (Google BLEU): métrica usada principalmente para evaluar modelos de traducción automática. Es especialmente útil en tareas donde es importante capturar todo el contenido de la referencia. Compara n-gramas entre la frase generada y la referencia (1 = coincidencia perfecta, 0 = sin coincidencia).
4. Generación de feedback explicativo con Mistral-7B-Instruct.


### **Ejemplo:**
Original: *“Tú debes seguir un estilo formal y preciso."*  
Corrección: *"Se debe seguir un estilo formal y preciso."*  
Feedback generado: *"La frase original utiliza el pronombre "tú" (debes) en un contexto formal, lo que resulta inapropiado. En textos académicos, es recomendable utilizar construcciones impersonales para mantener la objetividad y la distancia necesarias para un estilo formal. En lugar de "tú", se prefiere "se" para el pronombre personal, ya que este es más adecuado para referirse a un sujeto abstracto o impersonal. Además, es fundamental ajustar el verbo en tercera persona singular para mantener la concordancia verbal y evitar errores de número."*

### **Acknowledgements**
Financiado por la Comunidad de Madrid a través del convenio-subvención para el fomento y la promoción de la investigación y la transferencia de tecnología en la Universidad Carlos III de Madrid (PALABRIA-CM-UC3M)
