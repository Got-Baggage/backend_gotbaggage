[![Rails][rails]][rails-url] [![Postman][postman]][postman-url] [![Git][git]][git-url] [![Markdown][markdown]][markdown-url] [![PostgreSQL][postgreSQL]][postgresql-url] [![RSpec][rspec]][rspec-url]

[![Fly][fly]][fly-url] [![Miro][miro]][miro-url] [![CircleCI][circleci]][circleci-url] [![Visual Studio Code][visual studio code]][visual studio code-url] [![GraphQL][graphql]][graphql-url]

 <h1>Got Baggage?</h4>

<div align="center">
<img src="https://user-images.githubusercontent.com/106141130/207424425-56f48d40-ed60-46d5-b3ad-c5e87b4a99a6.png" alt="get-baggage-icon" width="350" /> </div>

Need help deciding what to pack for your trip? This application has prebuilt packing list's for your next adventure. 

This was a group CapStone project with a combined Front End and Back End team. For the first time students were given the opportunity to work collaboratively in an agile workflow to build an application. The project demonstrates knowledge we've gained throughout Turing as well as exploring new technologies. The Front End and Back End team implemented graphQL for the first time and used circle ci for continuous integration. 

The Back End application is an API that exposes endpoints to the Front End.

Front End Repository: [Got Baggage](https://github.com/Got-Baggage/fe-gotbaggage)

Deployed Application: [Got Baggage](https://fe-gotbaggage.vercel.app/)
<a name="readme-top"></a>

<h2> Table of Contents</h2>
<details open="open">
<summary>Table of Contents</summary>
  <ol>
    <li><a href="#technical-requirements"> Technical Requirements</a></li>
    <li><a href="#gems-and-tools"> Gems and Tools</a></li>
    <li><a href="#installation"> Installation</a></li>
    <li><a href="#schema"> Schema</a></li>
    <li><a href="#endpoints"> API Endpoints</a></li>
    <li><a href="#contributors"> Contributors</a></li>
  </ol>
</details>

<h2 id="technical-requirements">Technical Requirements</h2>
<ul>
<li>Ruby 2.7.4</li>
<li>Rails 5.2.8</li>
</ul>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h2 id="gems-and-tools">Gems and Tools</h2>
<ul>
  <li><a href="https://github.com/pry/pry">Pry</a></li>
  <li><a href="https://github.com/simplecov-ruby/simplecov">SimpleCov</a></li>
  <li><a href="https://www.rubydoc.info/gems/rack-cors/0.4.0">Rack CORS</a></li>
  <li><a href="https://github.com/thoughtbot/shoulda-matchers">Shoulda Matchers</a></li>
</ul>
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h2 id="installation"> Installation </h2>

To get started, clone the repo in your terminal by entering the following:

<ul>
  <li>git clone git@github.com:Got-Baggage/be_gotbaggage.git</li>
</ul>  
   
Once cloned, run the following commands:
<ul>
  <li>bundle install</li>
  <li>rails db:create</li>
  <li>rails db:migrate</li> 
  <li>rake load:all_items</li> 
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h2 id="schema"> Schema</h2>

<img width="487" alt="Database Schema" src="https://user-images.githubusercontent.com/98506079/207943301-2f84c763-92e8-4e84-8a5d-008c5f3b4340.png">
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h2 id="endpoints"> Endpoints</h2>
<details open="open">
<summary>Query/Mutation Example Responses</summary>
  <ol>
    <li><a href="#clear-all-trips"> Clear All Trips</a></li>
    <li><a href="#essential-category-items">Essential items and Items by Category("beach")</a></li>
    <li><a href="#all-trips">All Trips</a></li>
    <li><a href="#items-by-trip-id">Items by Trip ID</a></li>
    <li><a href="#create-trip">Create Trip</a></li>
    <li><a href="#create-item">Create Item</a></li>
    <li><a href="#update-item">Update Item</a></li>
    <li><a href="#category-names">Category Names</a></li>
    <li><a href="#delete-item">Deleting an item from a trip list</a></li>
    <li><a href="#delete-trip">Deleting a trip</a></li>
  </ol>
</details>

<h4 id="clear-all-trips">Clear All Trips</h4>

```javascript
mutation;
{
  clearTrips;
  {
    id;
  }
}
```

```javascript
sample response
  {
  "data": {
    "clearTrips": [
      {
        "id": "27"
      },
      {
        "id": "28"
      },
      {
        "id": "29"
      }
    ]
  }
}
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "essential-category-items">Essential items and Items by Category("beach")</h4>

```javascript
query
  {
  essentialItems{
    name
  }
  itemsByCategory(category: "beach")
  {
      name
    }
  }
```

```javascript
sample response
  {
  "data": {
    "essentialItems": [
      {
        "name": "Shampoo"
      },
      {
        "name": "Conditioner"
      }
    ],
    "itemsByCategory": [
      {
        "name": "Beach umbrella"
      },
      {
        "name": "Sunscreen "
      }
    ]
  }
}
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "all-trips">All Trips</h4>

```javascript
query
  {
    allTrips{
      name
      category
    }
  }
```

```javascript
sample response
  {
  "data": {
    "allTrips": [
      {
        "name": "Stevens Trip",
        "category": "city"
      },
      {
        "name": "Nicoles Disney Trip",
        "category": "city"
      },
      {
        "name": "Nikkys Cali Trip",
        "category": "city"
      }
    ]
  }
}
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "items-by-trip-id">Items by Trip ID</h4>

```javascript
query
  {
    itemsByTrip(tripId:1){
      name
      id
      category
    }
  }
```

```javascript
sample response
  {
  "data": {
    "itemsByTrip": [
      {
        "name": "Shampoo",
        "id": '1',
        "category": "essentials"
      },
      {
        "name": "Soap",
        "id": "2",
        "category": "essentials"
      },
      {
        "name": "sunglasses",
        "id": "3"
        "category": "beach"
      }
    ]
  }
}
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "create-trip">Create Trip</h4>

```javascript
mutation  {
  tripCreate(input: {name: "Baggage Trip", category: "camping", traveler: "britney spears"})
  {
    trip{
      id
      name
      category
      image
    }
  }
}
```

```javascript
response
  {
    "data": {
      "tripCreate": {
        "trip": {
          "name": "Baggage Trip",
          "category": "international",
          "traveler": "Stephen",
          "image": "https://www.lonestar.edu/images/internationalTravel.jpg"
        }
      }
    }
  }
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "create-item">Create Item</h4>

```javascript
mutation{
  itemCreate(input: {tripId: 1, itemName: "Medicine"})
  {
    item{
      name
      id
      category
    }
  }
}
```

```javascript
response
  {
    "data": {
      "itemCreate": {
        "item": {
          "name": "Medicine",
          "category": null,
          "id": "145"
        }
      }
    }
  }
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "update-item">Update Item</h4>

```javascript
mutation{
  itemUpdate(input: {id: 3, name: "mouth wash"})
  {
    item{
      name
      id
    }
  }
}
```

```javascript
response
  {
    "data": {
      "tripUpdate": {
        "item": {
          "name": "mouth wash",
          "id": "3"
        }
      }
    }
  }
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "category-names">Category Names</h4>

```javascript
query {
    categoryNames
    }
```

```javascript
response
{
  “data”: {
    categoryNames”: [
      “essentials”,
      “beach”,
      “camping”,
      “international”,
      “city”,
      “snowsports”,
      “roadtrip”
    ]
  }
}
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "delete-item">Deleting an item from a trip list</h4>

```javascript
mutation{
  tripItemDelete(input: {tripId: 1, itemID: 33})
  {
    tripItem{
      id
    }
  }
}
```

```javascript
response
  {
    "tripItemDelete": {
      "tripItemDelete": {
        "tripItem": {
          "id": "3"
        }
      }
    }
  }
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h4 id = "delete-trip">Deleting a trip</h4>

```javascript
mutation {tripDelete(input: {id:1})
  {
  trip{
    id
    }
  }
}
```

```javascript
response
  {
    "data": {
      "tripDelete": {
        "trip": {
          "id": "1"
        }
      }
    }
  }
```
<p align="right">(<a href="#readme-top">back to top</a>)</p>

<h2 id="contributors"> Contributors</h2>

<h3>Hazel Pablo</h3>

[![GitHub Badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Hpablo08)
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hazel-pablo-704779245/)

<h3>Beth Wilson </h3>

[![GitHub Badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/BethWProjects)
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/beth-wilson-92594284/)

<h3>Alycia Canavan </h3>

[![GitHub Badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/alyciacan)
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/alycia-canavan/)

<h3>Hunter Monroe</h3>

[![GitHub Badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/Hmonroe2/)
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/hunter-monroe-035ab0188/)

<h3>Nicole Esquer</h3>

[![GitHub Badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/nicole-esquer)
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/nicole-esquer)

<h3>Nikky Rojas</h3>

[![GitHub Badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/nikkyrojas/)
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/nikkyrojas/)

<h3>Stephen Fabian</h3>

[![GitHub Badge](https://img.shields.io/badge/GitHub-100000?style=for-the-badge&logo=github&logoColor=white)](https://github.com/stephenfabian)
[![LinkedIn Badge](https://img.shields.io/badge/LinkedIn-0077B5?style=for-the-badge&logo=linkedin&logoColor=white)](https://www.linkedin.com/in/stephen-fabian-5498658a/)


[Rails]: https://camo.githubusercontent.com/1ab1a7ec3f2dd01c7960044047e96a86aed5111004c9b0b86e852eac461bedac/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f527562795f6f6e5f5261696c732d4343303030303f7374796c653d666f722d7468652d6261646765266c6f676f3d727562792d6f6e2d7261696c73266c6f676f436f6c6f723d7768697465
[rails-url]: https://guides.rubyonrails.org/

[Postman]: https://camo.githubusercontent.com/3f0e26b0951bab845a1bb9a7198ecca0da272e462921b6edd85879f3673b6927/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f506f73746d616e2d4646364333373f7374796c653d666f722d7468652d6261646765266c6f676f3d706f73746d616e266c6f676f436f6c6f723d7768697465
[postman-url]: https://www.postman.com/

[Git]: https://user-images.githubusercontent.com/64919819/113648232-81d60d00-9649-11eb-8ea4-0ff5e399afb6.png
[git-url]: https://git-scm.com/doc

[Markdown]: https://camo.githubusercontent.com/510a057988cb5216f5d297ee202f6a08fa179798926cea28e95910f6b8ca5535/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f4d61726b646f776e2d3030303030303f7374796c653d666f722d7468652d6261646765266c6f676f3d6d61726b646f776e266c6f676f436f6c6f723d7768697465
[markdown-url]: https://www.markdownguide.org/

[PostgreSQL]: https://camo.githubusercontent.com/281c069a2703e948b536500b9fd808cb4fb2496b3b66741db4013a2c89e91986/68747470733a2f2f696d672e736869656c64732e696f2f62616467652f506f737467726553514c2d3331363139323f7374796c653d666f722d7468652d6261646765266c6f676f3d706f737467726573716c266c6f676f436f6c6f723d7768697465
[postgresql-url]: https://www.postgresql.org/docs/

[RSpec]: https://user-images.githubusercontent.com/64919819/113648167-6965f280-9649-11eb-8794-0f1082ae8d1c.png
[rspec-url]: https://rspec.info/documentation/

[fly]: https://custom-icon-badges.demolab.com/badge/Fly-DCDCDC?style=for-the-badge&logo=fly-io
[fly-url]: https://fly.io/
[miro]: https://img.shields.io/badge/Miro-050038?style=for-the-badge&logo=Miro&logoColor=white
[miro-url]: https://miro.com/
[circleci]: https://img.shields.io/badge/circle%20ci-%23161616.svg?style=for-the-badge&logo=circleci&logoColor=white
[circleci-url]: https://circleci.com/developer
[graphql]: https://img.shields.io/badge/-GraphQL-E10098?style=for-the-badge&logo=graphql&logoColor=white
[graphql-url]: https://graphql.org/
[visual studio code]: https://img.shields.io/badge/Visual%20Studio%20Code-0078d7.svg?style=for-the-badge&logo=visual-studio-code&logoColor=white
[visual studio code-url]: https://code.visualstudio.com/

<p align="right">(<a href="#readme-top">back to top</a>)</p>
