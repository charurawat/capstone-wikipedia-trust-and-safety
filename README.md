### Cyber Harassment Classification and Prediction of User Blocks in Wikipedia

#### This repo contains code part of my work for my capstone project on leveraging machine learning and deep learning to detect cyber harassment in the english wikipedia user community. This project is a part of the UVA MS Data Science Program and is sponsored by the Wikimedia Foundation. Note that this is work in progress. The project is expected to be completed by May 2019 and I will be putting up my code and work on this repo after completion of the project. I'm working on this project with 2 other grad students of UVA.
Please check https://meta.wikimedia.org/wiki/University_of_Virginia/Machine_learning_to_predict_Wikimedia_user_blocks to read more about the research project.

#### Files in this repo 

Currently the repo contains 2 files -

* xml_dump_parsing.ipynb - wikipedia dumps its data every month in form of xml files here (https://dumps.wikimedia.org/enwiki/) .
Refer to this article here (https://towardsdatascience.com/wikipedia-data-science-working-with-the-worlds-largest-encyclopedia-c08efbac5f5c)
which has instructions on extracting data in form of xml dumps using keras. My code in this notebook details the steps to follow thereafter.
In this notebook, I take in each XML file which is compressed and i decompress it and parse through it to extract contents from specific namespaces , namely the article and user namespace.
I have used the difflib library offered by mediawiki utilities (https://pythonhosted.org/mediawiki-utilities/) to compute "diffs" between each successive revision pertaining to an article because unfortunately
in the raw XML dumps, each edit or texxt pertaining to a user for an article is cumulative (includes all prior edits to that article) and this doesn't give us individual edits
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
        
 * eda_ipblocks.ipynb - contains some exploratory data analysis performed on the IPBLOCKS data sourced from wikipedia.
 The ipblocks data contains a record of all users ever blocked in english wikipedia (https://www.mediawiki.org/wiki/Manual:Ipblocks_table)


#### Project description:
The advent of the Internet can be easily heralded as one of the key events which
led to the “Information age” as it is colloquially known. Sharing of thoughts, ideas and opinions
reached new heights when people were able to engage in meaningful debates through online forums.
However, a darker aspect to this medium – online harassment, has become became rampant in these
communities. The Wikipedia user community is no stranger to this phenomenon. As of January 2019,
Wikipedia has 35 million users and on average 250k users register every month. Also, as per the
Wikipedia Community Engagement Insights 2018 report - 68% of the respondents reported having
experienced harassment at some point in the past and as a result about 22% of Wikipedians reported a
decrease in their contribution levels. To combat harassment, currently Wikipedia has an organic,
human-driven process in place, where cases of abuse reported are evaluated and enacted upon by
Wikipedia administrators. But relying on human evaluation works in some ways but it is not a solution
which scales with the growth of Wikipedia, as there were ~170k user blocks in 2018 alone.

Our goal is to develop a data-driven approach in combating cyber harassment that will address a
variety of issues that are otherwise faced by the human driven process, from errors and bias in human
judgement to efficiently evaluating a larger magnitude of cases. By analyzing user activity in form of
editing behavior and discussions, we will be able to predict users who are at risk of getting blocked in
the future.

Note that this is a research project in progress. I will be updating this repo with the code sometime in May 2019.
