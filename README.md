# Instalação do Microcks

https://microcks.io/documentation/installing/operator/

# Instalação API Curio Studio

# Ajuste o dominio no template em:

UI_ROUTE
API_ROUTE
WS_ROUTE
AUTH_ROUTE

# Crie o projeto e adicione o template

oc new-project nome_do_projeto

oc create -f apicurio-standalone-template.yml

oc process -f caminho_do_template.yaml

# Configure as variaveis

oc set env dc/apicurio-studio-api APICURIO_MICROCKS_API_URL=https://microcks.apps.cluster-qw5dp.qw5dp.sandbox660.opentlc.com/api

oc set env dc/apicurio-studio-api APICURIO_MICROCKS_CLIENT_ID=microcks-serviceaccount

oc set env dc/apicurio-studio-api APICURIO_MICROCKS_CLIENT_SECRET=ab54d329-e435-41ae-a900-ec6b3fe15c54

oc set env dc/apicurio-studio-ui APICURIO_MICROCKS_API_URL=https://microcks.apps.cluster-qw5dp.qw5dp.sandbox660.opentlc.com/api

oc set env dc/apicurio-studio-ui APICURIO_MICROCKS_CLIENT_ID=microcks-serviceaccount

oc set env dc/apicurio-studio-ui APICURIO_MICROCKS_CLIENT_SECRET=ab54d329-e435-41ae-a900-ec6b3fe15c54

oc set env dc/apicurio-studio-ui APICURIO_UI_FEATURE_MICROCKS=true

oc set env dc/apicurio-studio-ui JAVA_TOOL_OPTIONS=-Dapicurio-ui.feature.microcks=true
