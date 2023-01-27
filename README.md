# create repo urban-fiesta
#upload files (catalog.yaml, home.md, payments-oas.yaml
#im GitHub Reiter Actions --> New Workflow --> Simple flow --> Inhalt ersetzt --> commit
#API catalog cli auf virtueller Maschine?
#Anypoint Exchange API docu https://anypoint.mulesoft.com/exchange/portals/anypoint-platform/f1e97bc6-315a-4490-82a7-23abe036327a.anypoint-platform/exchange-experience-api/
#...
#catalog-cicd.yaml -> Publish API catalog to Exchange
#jobs:
  build:
    # Build Ubuntu
    runs-on: ubuntu-latest
    steps:
      - name: Check out repository code
        uses: actions/checkout@v3
      - name: Install api-catalog cli
        run: |
          sudo apt-get update
          npm install -g api-catalog-cli@latest
      - name: Publish API to Anypoint Exchange
        env: 
          ANYPOINT_CLIENTID: ${{ secrets.ANYPOINT_CLIENTID }} 
          ANYPOINT_CLIENTSECRET: ${{ secrets.ANYPOINT_CLIENTSECRET }}
          ANYPOINT_ORG_ID: ${{ secrets.ANYPOINT_ORGID }}
        run: |
          api-catalog publish-asset --force-update-metadata --organization="$ANYPOINT_ORG_ID" --client_id="$ANYPOINT_CLIENTID" --client_secret="$ANYPOINT_CLIENTSECRET"
#benötigt ANYPOINT_CLIENTID, ANYPOINT_CLIENTSECRET, ANYPOINT_ORGID von Platform
#gehe zu Settings --> secrets and variables --> für Actions --> ANYPOINT_CLIENTID, ANYPOINT_CLIENTSECRET, ANYPOINT_ORGID dort hinterlegen
#...?
#git clone https://andresc23jan23:Keyboard123.@anypoint.mulesoft.com/git/07aae032-dcf0-494f-84c0-656e3bee15c1/9ba49c1c-5cb8-49a2-8783-19095e143171
git clone https://USERNAME:PASSWORD@APIURL
https://github.com/adam-p/markdown-here/wiki/Markdown-Cheatsheet
#..? wo gebe ich den Teil ein, gefühlt in Exchange!? === Invoice Flex Payment System API

Publishing to Exchange...
API successfully published... ✅
Group ID:     ***
Asset ID:     invoice-payment-system-api
Version:      1.1.0
Exchange URL: https://anypoint.mulesoft.com/exchange/***/invoice-payment-system-api

#...? wie in die Platform?
#Anypoint Exchange: Invoice Flex Payment System API? wie in die Platform? exchange..publish new asset... REST API...paymentas-oas.yaml
