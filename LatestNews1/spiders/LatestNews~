from scrapy.contrib.spiders import CrawlSpider #make sure you have Scrapy libraries installed.
from scrapy.selector import Selector

class MySpider(CrawlSpider):
    name = 'LatestNews' 
    allowed_domains = ['http://www.google.co.in']
    start_urls = ['http://news.google.co.in']

    

    def parse(self, response):
        self.log('Hi, this is an item page! %s' % response.url)
	sel = Selector(response)
        site = sel.xpath('//td[@class="esc-layout-article-cell"]') #selects the full news layout http://news.google.co.in
        for i in site:
		a = i.xpath('div[@class="esc-lead-article-title-wrapper"]/h2/a/span/text()').extract()
		b = i.xpath('div[@class="esc-lead-article-source-wrapper"]/table/tbody/tr/td[@class="al-attribution-cell source-cell"]/span/text()').extract()
		if(len(a)!=0):	#necessary to avoid OutOfBoundException	.
			print a[0] #Items can be used here.
		if(len(b)!=0):
			print b[0]
		print '\n'
        
