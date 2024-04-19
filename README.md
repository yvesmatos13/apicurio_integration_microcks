# Criação do projeto 

oc new-project api-designer

# Instalação do operador Microcks

https://microcks.io/documentation/installing/operator/

# Instalação do Microcks

oc apply -f microcks-install.yaml

# Instalação API Curio Studio

# Ajuste o dominio no template em:

UI_ROUTE
API_ROUTE
WS_ROUTE
AUTH_ROUTE

# Crie o projeto e Adicione o template

oc create -f apicurio-standalone-template.yml

oc process apicurio-studio-standalone | oc apply -f -

# Configure as variaveis

oc set env dc/apicurio-studio-api APICURIO_MICROCKS_API_URL=https://microcks.apps.cluster-qw5dp.qw5dp.sandbox660.opentlc.com/api

oc set env dc/apicurio-studio-api APICURIO_MICROCKS_CLIENT_ID=microcks-serviceaccount

oc set env dc/apicurio-studio-api APICURIO_MICROCKS_CLIENT_SECRET=ab54d329-e435-41ae-a900-ec6b3fe15c54

oc set env dc/apicurio-studio-ui APICURIO_MICROCKS_API_URL=https://microcks.apps.cluster-qw5dp.qw5dp.sandbox660.opentlc.com/api

oc set env dc/apicurio-studio-ui APICURIO_MICROCKS_CLIENT_ID=microcks-serviceaccount

oc set env dc/apicurio-studio-ui APICURIO_MICROCKS_CLIENT_SECRET=ab54d329-e435-41ae-a900-ec6b3fe15c54

oc set env dc/apicurio-studio-ui APICURIO_UI_FEATURE_MICROCKS=true

oc set env dc/apicurio-studio-ui JAVA_TOOL_OPTIONS=-Dapicurio-ui.feature.microcks=true
