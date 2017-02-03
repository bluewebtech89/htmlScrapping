# htmlScrapping

lxml is a pretty extensive library written for parsing XML and HTML documents very quickly, even handling messed up tags in the process. We will also be using the Requests module instead of the already built-in urllib2 module due to improvements in speed and readability. You can easily install both using pip install lxml and pip install requests.

After a quick analysis, we see that in our page the data is contained in two elements - one is a div with title ‘buyer-name’ and the other is a span with class ‘item-price’:

Carson Busses
$29.95

Knowing this we can create the correct XPath query and use the lxml xpath function like this:

This will create a list of buyers:

buyers = tree.xpath('//div[@title="buyer-name"]/text()')

This will create a list of prices

prices = tree.xpath('//span[@class="item-price"]/text()') Let’s see what we got exactly:

print 'Buyers: ', buyers print 'Prices: ', prices Buyers: ['Carson Busses', 'Earl E. Byrd', 'Patty Cakes', 'Derri Anne Connecticut', 'Moe Dess', 'Leda Doggslife', 'Dan Druff', 'Al Fresco', 'Ido Hoe', 'Howie Kisses', 'Len Lease', 'Phil Meup', 'Ira Pent', 'Ben D. Rules', 'Ave Sectomy', 'Gary Shattire', 'Bobbi Soks', 'Sheila Takya', 'Rose Tattoo', 'Moe Tell']

Prices: ['$29.95', '$8.37', '$15.26', '$19.25', '$19.25', '$13.99', '$31.57', '$8.49', '$14.47', '$15.86', '$11.11', '$15.98', '$16.27', '$7.50', '$50.85', '$14.26', '$5.68', '$15.00', '$114.07', '$10.09']
