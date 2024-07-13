# Support Ticket Categorization System with NLP

## Problem Statement
In today's dynamic business landscape, organizations are increasingly recognizing the pivotal role customer feedback plays in shaping the trajectory of their products and services. The ability to swiftly and effectively respond to customer input not only fosters enhanced customer experiences but also serves as a catalyst for growth, prolonged customer engagement, and the nurturing of lifetime value relationships. As a dedicated Product Manager or Product Analyst, staying attuned to the voice of your customers is not just a best practice; it's a strategic imperative.

## Business Context
While your organization may be inundated with a wealth of customer-generated feedback and support tickets, your role entails much more than just processing these inputs. To make your efforts in managing customer experience and expectations truly impactful, you need a structured approach – a method that allows you to discern the most pressing issues, set priorities, and allocate resources judiciously. One of the most effective strategies at your disposal is to harness the power of Support Ticket Categorization.

## Objective
Develop an advanced support ticket categorization system that accurately classifies incoming tickets, assigns relevant tags based on their content, implements mechanisms and generate the first response based on the sentiment for prioritizing tickets for prompt resolution.

## Getting Started

### Prerequisites
- Python 3.x
- Jupyter Notebook
- Required Python libraries (can be installed via `requirements.txt`)

### Installation
1. Clone the repository:
    ```bash
    git clone https://github.com/vampokala/NLP_SupportTicketCategorization.git
    cd NLP_SupportTicketCategorization
    ```

2. Create a virtual environment and activate it:
    ```bash
    python3 -m venv venv
    source venv/bin/activate  # On Windows, use `venv\Scripts\activate`
    ```

3. Install the required libraries:
    ```bash
    pip install -r requirements.txt
    ```

### Running the Notebook
1. Start Jupyter Notebook:
    ```bash
    jupyter notebook
    ```

2. Open the `NLP_SupportCategorization.ipynb` notebook and run the cells sequentially.

## Language Model Used
The notebook utilizes a pre-trained language model for natural language processing tasks. Key highlights include:
- **Model**: mistral-7b-instruct-v0.2.Q6_K.gguf
- **Purpose**: Used for text classification, sentiment analysis, and generating responses.
- **Features**: 
  - High accuracy in text classification tasks.
  - Capable of understanding context and generating human-like responses.
  - Pre-trained on a large corpus of text data, making it adaptable to various NLP tasks.
- **Performance**: Demonstrated high performance in categorizing support tickets and generating relevant tags.

## Steps performed in Automating with LLM
### Task1 - Auto generate Tags and category
The following prompt is used to instruct the LLM to read the Support text and create the tags and category.
prompt_2 = """
  You are a Product Analyst, Classify the Support ticket based on the Support Ticket Text presented in the input into the following categories and not any other.
  - Technical issues
  - Hardware issues
  - Data recovery
  Create a new column 'Tags' in the dataframe, populate with compelling tags for each ticket category.
  Format the output as a JSON object with a single key-value pair as shown below::
  {"Tags": "tags_prediction"}
"""
### Task2 - Assign Prioirty and ETA
The following prompt is used to instruct the LLM to read the Support Text, tags, Category and generate the prioirty and ETA
prompt_3 = """
    You are provided a Support ticket,Category and Tags as input. Based on the text in the ticket,category and tags provided for the ticket,
    identify the following:
      - Priority of resolving the ticket
      - ETA for resolving the ticket

    Instructions:
    1.Priority High, Medium and Low are based on sentiment of the support ticket text.
    2.ETA Immidiate, 1-2 days, 2-3 days, 3-4 days are based on the number of days it takes to resolve the ticket.
    3.
    4.

     Return in this format: {"Priority": "priority_prediction", "ETA": "eta_prediction"}
"""
### Task3 - Create a Draft Response
Use the following prompt and generate the a draft response
prompt_4 = """
    You are provided a Support ticket, Category of the ticket,Tags,the Priority with which it has to be resolved, and the ETA for resolution. Based on this information, draft a response that can be shared with the customer.

    Instructions:
    1. For urgent needs, start with 'I apologize for the inconvinience..'
    2. For remaining categories, draft a compelling response with instructions and a positive tone.
    3.
    4.
    5. The number of words in the response should be less than 48.

    Return only the response that has to be shared with the customer.
"""




## Notebook Structure
1. **Problem Statement**: Explanation of the problem and its importance.
2. **Business Context**: Detailed description of the business context and need for categorization.
3. **Objective**: Goals and objectives of the categorization system.
4. **Data Preparation**: Steps for preparing the data for analysis and model building.
5. **Model Development**: Developing machine learning models for categorization and sentiment analysis.
6. **Evaluation**: Evaluating the performance of the models.
7. **Deployment**: Steps for deploying the model (if applicable).

## Contributing
Pull requests are welcome. For major changes, please open an issue first to discuss what you would like to change.

## License
[MIT](https://choosealicense.com/licenses/mit/)
