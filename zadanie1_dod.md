1.  Utworzenie buildera BuildKit opartego na docker-container.
  
2.  W pliku Dockerfile_dod znajduję się ustawienia potrzebne przy tworzeniu obrazów pobieranych z GitHub.

3.  Za pomocą polecenia zbudowano obraz i cache
   docker buildx build -f Dockerfile_dod \
  --platform linux/amd64,linux/arm64 \
  --sbom \
  --provenance=mode=max \
  -t docker.io/<USER>/lab:pogoda \
  --cache-to type=registry,ref=docker.io/<USER>/cache_pogoda,mode=max \
  --cache-from type=registry,ref=docker.io/<USER>/cache_pogoda \
  --push https://github.com/WikMat02/ProgApChZAD1.git

4. Potwierdzenie działania za pomocą:
   docker buildx imagetools inspect docker.io/<USER>/lab:pogoda
   docker buildx imagetools inspect docker.io/<USER>/cache_pogoda

