# Route Hunter / Flyer

MVP estático del juego de aviación para GitHub Pages.

## Incluye
- PWA estática sin backend ni base de datos.
- Mapa MapLibre/OpenStreetMap.
- Aciertos, fallos, precisión, vidas, hangar y viaje.
- Rondas de 5 opciones con regla: exactamente 1 VALID, 4 INVALID, 0 UNKNOWN.
- Tests + fuzz test.
- GitHub Actions para test/deploy y refresh.
- Generador desde `data/raw/flights.json`.

## Importante
`data/china/JUZ.json` es una demo de integración, no una certificación aeronáutica de todas las opciones. Para datos reales, añade un adaptador permitido en `generator/sources/` o genera `data/raw/flights.json` desde una fuente pública compatible. Nunca conviertas ausencia de datos en `INVALID`; debe ser `UNKNOWN`.

## Subir a tu repo
Repo: `https://github.com/memevialino/flyer`

1. Descomprime el ZIP.
2. Copia TODO su contenido en la raíz del repo.
3. Commit/push a `main`.
4. GitHub → Settings → Pages → Source: **GitHub Actions**.
5. Abre Actions y comprueba `Deploy Route Hunter`.
6. La URL esperada será `https://memevialino.github.io/flyer/`.

## Probar localmente
```bash
npm test
python3 -m http.server 8080
```
Abre `http://localhost:8080`.

## Generar packs desde datos normalizados
```bash
cp data/raw/flights.example.json data/raw/flights.json
npm run refresh
```

## Siguiente fase
Conectar 1–2 adaptadores web públicos permitidos y añadir fixtures para comprobar que cambios de HTML no generen rondas falsas.
