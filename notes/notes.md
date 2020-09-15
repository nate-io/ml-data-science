# Types Of Machine Learning 

## In order to ensure good results you must fit the proper ML type to the problem you are trying to solve
<ol>
  <li style='color: #007ba7;'>Supervised Learning</li>
    Data is labeled and the algorithm attempts to choose the correct label for new data. If wrong, it tries again. Sub-types:
    <ul>
      <li>Classification - is this data one thing or another e.g., is this person at risk of heart disease? Two flavors - binary (one of two options) or multi-class (more than two options e.g., what kind of dog breed?)</li>
      <li>Regression - predictive numerical guess e.g., How much will a house sell for based on characteristics (neighborhood, square footage, number of rooms, etc.)?</li>
    </ul>
  <li style='color: #007ba7;'>Unsupervised Learning</li>
    Suppose you work at an ecommerce company and the marketing department wants to figure out where to send an email campaign in order to sell a certain class of goods such as winter clothing. Given a list of customers and their corresponding past purchases, you can use unsupervised learning to divide and group the customer list into segments which can indicate likelihood to make a purchase of the goods. Dividing the list like this is called clustering. Recommendation engines can often start out as unsupervised learning problems.
  <li style='color: #007ba7;'>Transfer Learning</li>
    Using an existing ML model to inform another, related, problem type. For instance, say you had a problem where you wanted a system to identify cars & dogs in photos. If you already have a model which identifies cars then you can repurpose & fine-tune the model to also identify the dogs rather than building an entirly new model from scratch. This is important because training these models can be expensive due to the number of calculations required for good results.
  <li style='color: #007ba7;'>Reinforcement Learning</li>
    Training a model to perform a task and then rewarding or punishing the model based on the result. The reward/punishment can be as simple as incrementing/decrementing a score value with the end result being the highest score wins. This is what the famous DeepMind Go AI used. Although impressive it has yet to find many common applications in the business world.
</ol>

## Simple questionnaire to determine learning type fit:
1. "I know my inputs and outputs" ==> ```Supervised Learning```
2. "I know my inputs but not sure of my outputs" ==> ```Unsupervised Learning```
3. "This problem is similar to something else" ==> ```Transfer Learning```
