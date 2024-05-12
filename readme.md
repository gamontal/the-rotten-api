## ⚠️ This repository is no longer maintained.

# The Rotten API

`the-rotten-api` is a Node.js wrapper for the [Rotten Tomatoes API v1.0](http://developer.rottentomatoes.com/docs).

## Installation

```
$ npm install --save the-rotten-api
```

## Usage Examples

#### Movie search:

```javascript
var rt = require('the-rotten-api');
rt.apiKey('your-api-key');

rt.movies('in_theaters', function(err, data) {
  if (err) { console.log(err); }
  
  console.log(data);
  
  /*
  { 
       id: '771321699',
       title: 'Star Wars: Episode VII - The Force Awakens',
       year: 2015,
       mpaa_rating: 'PG-13',
       runtime: 136,
       critics_consensus: '',
       release_dates: [Object],
       ratings: [Object],
       synopsis: 'The Star Wars saga continues with this seventh entry -- the first under the Walt Disney Co. umbrella. The film will act as the start of a new trilogy set after the events of Return of the Jedi. J.J. Abrams directs from a script by Michael Arndt. ~ Jeremy Wheeler, Rovi',
       posters: [Object],
       abridged_cast: [Object],
       alternate_ids: [Object],
       links: [Object] 
  },
  ...
  */
}
```

#### Movie info:

```javascript
var rt = require('the-rotten-api');
rt.apiKey('your-api-key');

var movieId = 12897;

rt.info(movieId, function(err, data) {
  console.log('Title: ' + data.title);
  console.log('Year: ' + data.year);
}

/*
    Title: The Matrix
    Year: 1999
*/
```

## Methods

#### `Search`

Search for movies.

`.search(query | [options], callback)`

***Options:***

Name | Description | Type | Required |
-----|------------ |------|----------|
query| The plain text search query to search for a movie.| `String` | Yes |
page | The selected page of movie search results | `Number` | No |
pageLimit | The amount of movie search results to show per page | `Number` | No |


#### `Lists`

Rotten Tomatoes available lists.

`.lists(directory, callback)`

Name | Description | Type | Required |
-----|------------ |------|----------|
movies| Shows the movie lists we have available | `String` | No |
dvds | Shows the DVD lists we have available | `String` | No |
`empty string` | Displays the top level lists available in the API. | `String` | Yes |

#### `info`

Detailed information on a specific movie specified by Id. You can also limit the results to `cast` and `reviews`.

`.info(id | [options], callback)`

Name | Description | Type | Required |
-----|------------ |------|----------|
id | The movie's id | `Number` | Yes |
limitTo | `cast` or `reviews` | `String` | No |

#### `movies`

`.movies(list | [options], callback)`

Search for a specific list of movies.

Name | Description | Type | Required |
-----|------------ |------|----------|
list| `box_office`, `in_theaters`, `opening`, `upcoming`| `String` | Yes |
limit | Limits the number of box office movies returned | `Number` | No |
page | The selected page of in theaters movies | `Number` | No |
country | Provides localized data for the selected country (ISO 3166-1 alpha-2) if available. Otherwise, returns US data. | `String` | No |
## Contribution

Contributions are welcome.

`git clone` the Github repository:

```
$ git clone https://github.com/gmontalvoriv/the-rotten-api.git
```

## License

[MIT](https://github.com/gmontalvoriv/nyt-top/blob/master/LICENSE)

