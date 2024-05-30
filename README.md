**Rezultat:**
![lab 8 do 6 slajd](https://github.com/erkjx/zadanie2/assets/129630909/94c6f7f9-1d23-4329-84dd-488088028f9f)
![lab8 7-9](https://github.com/erkjx/zadanie2/assets/129630909/b4bde868-a1dd-4844-afae-2cc00316a9ba)
![lab9 1-3](https://github.com/erkjx/zadanie2/assets/129630909/44c40d58-1090-4234-a3af-00e766f2b608)
![lab9 3](https://github.com/erkjx/zadanie2/assets/129630909/cc442a34-c3c3-456f-9062-c4fb4f1e9516)
![lab9 slajd 4](https://github.com/erkjx/zadanie2/assets/129630909/57f29668-cd67-4581-8105-049d01599562)
![lab9 slajd 4 1](https://github.com/erkjx/zadanie2/assets/129630909/cae8d7d7-a920-4edf-b9f5-c888ef0786d2)
![lab9 slajd 9](https://github.com/erkjx/zadanie2/assets/129630909/c9e7d068-9e81-41d3-8044-819ca2f7005c)

**Wyniki skanowania:**
![skan1](https://github.com/erkjx/zadanie2/assets/129630909/a60a2e62-2033-4bbc-bcd8-fdc332acab7d)
![skan2](https://github.com/erkjx/zadanie2/assets/129630909/dfcf85d7-44c4-4a4c-8975-7a26ad626952)
![skan3](https://github.com/erkjx/zadanie2/assets/129630909/9d3fae35-b30e-4979-ac30-1fb743e28334)
![skan4](https://github.com/erkjx/zadanie2/assets/129630909/15ed2c48-2ac3-4be5-8e55-41afe7754aec)
![wynik s](https://github.com/erkjx/zadanie2/assets/129630909/cb40e458-c447-4c54-8fcb-f1acf5f892a9)

**Omówienie dokonanych zmian przy dodawaniu skanowania Docker Scout:**  
**Nazwa kroku:** 
 * name: Scan local image  
**Uniklany identyfikator kroku:**  
  * id: image-scan  
 Pobiera skrypt instalacyjny Docker Scout CLI z GitHub i zapisuje go jako install-scout.sh.  
  * curl -fsSL https://raw.githubusercontent.com/docker/scout-cli/main/install.sh -o install-scout.sh  
**Logowanie do Docker Hub:**  
  * docker login -u ${{ vars.DOCKERHUB_USERNAME }} -p ${{ secrets.DOCKERHUB_TOKEN }}  
**Instalacja Docker Scout:**  
  * sh install-scout.sh  
**Uruchamia skanowanie obrazu Docker o nazwie erkjx/zadanie2:zadanie2 w celu wykrycia luk bezpieczeństwa.  
Opcje:**  
 * --exit-code ustawia kod wyjścia na wartość określającą wynik skanowania;  
 * --only-severity critical,high ogranicza skanowanie do krytycznych i wysokich zagrożeń;  
  * docker scout cves --exit-code --only-severity critical,high erkjx/zadanie2:zadanie2  
**Zapisywanie wyniku skanowania:**  
  * echo "SCAN_RESULT=$?" >> "$GITHUB_ENV"  
