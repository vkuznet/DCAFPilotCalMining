Mining Data from Calendar

* Description

In this project, we would like to extract some information from physicists' calendars, which will be used for predicting the datasets used in their near future research.

Physicists' calendars contain research conferences which they have attended or plan to. Past calendar information can be used for building statistical models, and future calendar information can be used as predictors for prediction.

* Design

The canlendar data will probably be provided as a (relational?) database from CERN.

In the first step, we will extract from physicists' calendars the number of conferences in each time slot (e.g. per week or month) (and ...?).
Different conferences may have different numbers of talks, and we will assign a bigger weight to a conference which has more talks.
Q:
We don't extract different information from calendars for different datasets?
Are we to study the relation between calendars and all the datasets (not individual dataset)?

In the second step, we will model the relation between the dataset access by physicists and their calendar information over the time. My tentative plan is to choose an appropriate (multivariate) time series or online learning model.

* tools

I plan to program mainly in Python. To perform queries on the given database, I may use some database driver module.

For statistical modelling the data, I would like to program in R (or Python), to utilize R's statistical and machine learning packages (or NumPy, SciPy, sklearn modules in Python)

For gluing scripts and commands together, I plan to use bash script (or Python).

* skeleton code

The followings are declarations of some functions in Python.

** Parsing CMS calendar database dump

def parse_schema(fschema):
    """parse a schema file for the type of each field
    input: a schema file
    output: an ordered dictionary of each schema attribute and its type

def parse_dataframe_by_match_record(fdataframe, attribute2type):
    """  parse dataframe, by specifying each record and reach field
    input: a dataframe file, and an ordered dict of each schema attribute and its type
    output: a list of dicts, each of which is the parsed result of each conference by the schema
    allow PRES_TITLE field span more than one lines, and assume other fields can't span more than one line
    """

** Data analysis

def count_conf(conf_db)
    """ extract conference counts in time slots (weeks) from calendar database
    input: conference data in some database
    output: a list (or dictionary) of pairs, each pair is (week_str, ct_int), where ct_int is the number of conferences (or even talks) in the week specified by string week_str.
    """

def build_model(conf_ct, data_access)
    """build a statistical model between conference count per time slot and dataset accesses per time slot
    input:
    conf_ct is the output of count_conf
    data_access is a dataframe containing information about physicists accessing the datasets.
    output:
    a statistical model modeling their relations
    """
    
def predict(model, conf_ct, )
    """ predict dataset accesses from conference count in the future time slot, using a model
    input:
    model is a model  built by build_model().
    conf_ct is the conference count in the future time slot
    output:
    dataset accesses in the future time slot
    """