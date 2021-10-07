# desafio04-ignite-reactjs

## Desafio 04: Upload de imagens

### Sobre o desafio:

Nesse desafio, você deverá criar uma aplicação para treinar o que aprendeu até agora no ReactJS

Essa será uma aplicação onde o seu principal objetivo é adicionar alguns trechos de código para que a aplicação de upload de imagens funcione corretamente. Você vai receber uma aplicação com muitas funcionalidades e estilizações já implementadas. Ela deve realizar requisições para sua própria API Next.js que vai retornar os dados do FaunaDB (banco de dados) e do ImgBB (serviço de hospedagem de imagens). A interface implementada deve seguir o layout do Figma. Você terá acesso a 4 arquivos para implementar:

- Infinite Queries e Mutations com React Query;
- Envio de formulário com React Hook Form;
- Exibição de Modal e Toast com Chakra UI;
- Entre outros.

## React Query

Na aplicação do desafio, você vai lidar com Infinite Queries, Mutations e Invalidações. Abaixo pode-se entender um pouquinho o papel de cada uma delas na aplicação:

- **Infinite Queries**: Listagem que adiciona mais dados ao clicar em um botão de carregamento ou "infinite scroll". Ela será utilizada nessa aplicação para realizar o carregamento das imagens cadastradas no nosso banco. O carregamento foi implementado com um clique em um botão, não o "infinite scroll" (já fica aí a sugestão de um extra para o desafio).
- **Mutations**: Diferente das queries do React Query que são utilizadas normalmente para a busca de dados, as mutations são responsáveis pela criação/edição/remoção de dados. Ela será utilizada nessa aplicação para o cadastro de uma nova imagem no banco.
- **Invalidações**: Utilizada para marcar manualmente uma query como `stale` e forçar a atualização dos dados. Ela será utilizada nessa aplicação para marcar a query de listagem de imagens como `stale` quando a mutation de cadastrar uma nova imagem ocorrer com sucesso.

Caso queira se aprofundar nesse assunto, acesse os links, pois podem te ajudar

[Infinite Queries](https://react-query.tanstack.com/guides/infinite-queries)

[Mutations](https://react-query.tanstack.com/guides/mutations)

[Invalidation from Mutations](https://react-query.tanstack.com/guides/invalidations-from-mutations)

## React Hook Form

Na aplicação do desafio, você vai precisar implementar o registro dos inputs do formulário de cadastro da imagem, as validações e enviar os erros desses inputs.

Diferentemente do que foi visto na jornada, dessa vez você deve trabalhar com as validações diretamente no React Hook Form em vez de utilizar um `resolver` do Yup.

Caso queira se aprofundar nesse assunto, deixaremos aqui um link que pode te ajudar:

[useForm - register](https://react-hook-form.com/api/useform/register)

## ImgBB

Para o armazenamento das imagens do desafio, decidimos utilizar uma solução de hospedagem de arquivos gratuita e de fácil utilização chamada ImgBB. Não é a melhor solução para esse tipo de hospedagem, mas é a mais fácil pra vocês conseguirem implementar.

Portanto, para conseguir realizar os uploads das imagens para essa plataforma você precisar seguir 3 passos:

1. [Criar uma conta](https://imgbb.com/login) no ImgBB;
2. [Criar a sua chave](https://api.imgbb.com/) da API;
3. Copiar o valor dessa chave e colar no seu `.env.local` da seguinte forma:

`NEXT_PUBLIC_IMGBB_API_KEY=VALOR_DA_CHAVE_COPIADA`

Com esses três passos, você deve conseguir realizar o upload dessas imagens para o ImgBB normalmente. Caso tenha dúvidas, dê uma olhada no link abaixo:

[Upload Image - Free Image Hosting](https://api.imgbb.com/)

## FaunaDB

Para o armazenamento das informações das imagens (url, título e descrição), decidimos utilizar o FaunaDB já utilizado por você ao longo da jornada. Tudo que você precisa fazer é criar um banco no FaunaDB com um nome de sua preferência que **precisa** ter uma coleção chamada `images`. Com o banco e coleção criados, basta você criar e copiar a chave do banco no seu arquivo `.env.local` da seguinte forma:

`FAUNA_API_KEY=VALOR_DA_CHAVE_COPIADA`

Dessa forma você deve conseguir realizar o cadastro das informações das imagens no FaunaDB. Caso tenha dúvidas, reassista as aulas sobre a configuração do FaunaDB ou dê uma olhada no link abaixo:

[Welcome to the Fauna documentation!](https://docs.fauna.com/fauna/current/start/index.html)

## API do Next.js

Nesse desafio toda a API do Next.js já foi implementada para você, porém vamos explicar rapidamente o que foi feito nessa etapa para que você entenda os dados que deve enviar e os dados que irá receber ao realizar as requisições.

- **GET api/images**: Essa é a rota utilizada para listagem das imagens. Ela rota recebe um `query param` de nome `after` que indica caso haja mais dados a serem carregados do FaunaDB. Por padrão, foi definido que a paginação da resposta do FaunaDB é de 6 dados. A resposta da API é um `json` com dois valores:
    - **data**: Dados formatados das imagens cadastradas no FaunaDB, exemplo:
        
        ```jsx
        "data": [
        	{
        	  "title": "Doge",
            "description": "The best doge",
            "url": "https://i.ibb.co/K6DZdXc/minh-pham-LTQMgx8t-Yq-M-unsplash.jpg",
            "ts": 1620222828340000,
            "id": "294961059684418048"
        	},
        ]
        ```
        
    - **after**: Referência da próxima página de dados caso tenham mais imagens a serem carregadas do FaunaDB. Caso contrário, retorna `null`.
- **POST api/images**: Essa é a rota utilizada para cadastro das informações da imagem (url, título e descrição) no FaunaDB. Tudo que você precisa enviar são esses três dados pelo `body` que o cadastro irá ocorrer e, caso dê tudo certo, retornará uma mensagem `success: true`.

## Resultado final do desafio

### Prints

![image](https://user-images.githubusercontent.com/74268252/136366660-a5bf72f5-510e-4c04-9237-c874613b030e.png)

![image](https://user-images.githubusercontent.com/74268252/136366731-238645e4-47f6-441b-ba64-dfe734613fe4.png)

![image](https://user-images.githubusercontent.com/74268252/136366834-9856c734-92bd-41f4-94bf-6f1b5a3f64de.png)

![image](https://user-images.githubusercontent.com/74268252/136366913-8c9185d9-73a3-46a9-8794-c73e7eb3e05f.png)

![image](https://user-images.githubusercontent.com/74268252/136367039-ad5f8136-4e1d-4274-a08b-764aa47125d9.png)

![image](https://user-images.githubusercontent.com/74268252/136367093-ea388fc6-1b51-4576-9f67-8492ffbd6606.png)

![image](https://user-images.githubusercontent.com/74268252/136367176-704176db-86c4-41af-ad4d-515ebf8a6a5c.png)

### Link para post de apresentação

https://www.linkedin.com/feed/update/urn:li:activity:6851823318316711936/
