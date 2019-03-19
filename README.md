### Parsing XML dumps from Wikipedia


* xml_dump_parsing.ipynb - wikipedia dumps  data every month in form of xml files here (https://dumps.wikimedia.org/enwiki/) .
Refer to this article [here](https://towardsdatascience.com/wikipedia-data-science-working-with-the-worlds-largest-encyclopedia-c08efbac5f5c) 
which has instructions on extracting data in form of xml dumps using keras. My code in this notebook details the steps to follow thereafter.
In this notebook, I take in each XML file which is compressed and i decompress it and parse through it to extract contents from specific namespaces , namely the article and user namespace.
I have used the difflib library offered by mediawiki utilities (https://pythonhosted.org/mediawiki-utilities/) to compute "diffs" between each successive revision pertaining to an article because unfortunately
in the raw XML dumps, each edit or text pertaining to a user for an article is cumulative (includes all prior edits to that article) and this doesn't give us individual edits
by users. The output of this code is a dataframe wherein each user has text that pertains only to his edit of the article. It is dumped into a csv.
These csv files are each > 1.5 GB.

Understanding the iteration in the XML dumps -

class mw.xml_dump.Iterator(site_name=None, base=None, generator=None, case=None, namespaces=None, pages=None)
XML Dump Iterator. Dump file meta data and a Page iterator. Instances of this class can be called as an iterator directly. E.g.:
(from mw.xml_dump import Iterator

    # Construct dump file iterator
      dump = Iterator.from_file(open("example/dump.xml"))

    # Iterate through pages
      for page in dump:

        # Iterate through a page's revisions
        for revision in page:
            print(revision.id))
        
