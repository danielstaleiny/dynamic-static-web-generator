# dynamic-static-web-generator

Create all the static website with https://www.11ty.io/

all the dynamic content needed for meta content needs to be observe and updated on change of the content. for example. page of the profile. once profile is added/edited/remove page need to be updated. create redis hashes of the object to compare the data. or create queue to worker to update static sites for each profile changed. Dynamic content is not so dynamic if it doesn't change every second. 

For the content which changes everysecond, use sockets and js in the client.

for search use js in the frontend.
auth cookies, and js 
everything else should be generated from db as static page. 

monitor how many documents changes on every job request. make sure that once static page is replace the cache is reset. 


3 levels of content.
 - static content 
 - rarely updated dynamic content -> pre-generated and once content is updated, update the static site. use *reverse cache.
 - often updated dynamic content -> generated in place. basically ssr. use cache, caching in redis.
 
use js in client to fill the wholes. 

on the server/disk ignore the url values. 

Think about the auth, and how it changes the content depending on user authenticated. 

*reverse cache is when changes happen and then the static site is rebuild based on new updated data. caching in the static generated pages.



how to notify worker to regenerate static files, and which one.

either configure server to notify worker. like queue. or make a cronjob to retrieve the newest stuff every *time period*

compare object hash, like a snapshot and decide what to re-generate.
