# Estructura de carpetas del sistema (a construir)
```
curso-mantenimiento/
├── config/            # voz, avatar, estilo de marca, música, claves (.env, nunca compartir)
├── listado_maestro.csv  # lecciones y estado: pendiente / en_guion / aprobado / producido / publicado
├── prompts/           # director, investigador, pedagogico, guionista, revisor, seo
├── agentes/
│   ├── agi01_director.py      ├── agi06_visual.py
│   ├── agi02_investigador.py  ├── agi07_narrador.py
│   ├── agi03_pedagogico.py    ├── agi08_editor/  (plantilla Remotion)
│   ├── agi04_guionista.py     ├── agi09_publicador.py
│   └── agi05_revisor.py       └── agi10_analista.py
├── control_calidad.py
├── aprobacion_whatsapp.py
├── salida/V02/        # ficha.json, guion.json, guion.pdf, voz.mp3, escenas/, final.mp4, final.srt, miniatura.png
└── orquestador.py     # toma la siguiente lección pendiente y ejecuta la cadena
```
