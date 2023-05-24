# Fleksja

Fleksja is a web application created with a ReactJS front end and a Django-Rest-Framework backend. It is designed to provide Polish language exercises generated programmatically using Morfeusz2, a morphological analyzer and generator.



## Approach

1. **Source of High-Quality Polish Text:** Polish literature in the public domain was used as a source of high-quality Polish text.

2. **Word Form Generation:** Morfeusz2 was utilized to generate various word forms of any given word.

3. **Conversion to Morphology Exercise:** Polish passages were transformed into grammar exercises by automatically converting a percentage of words into dropdown multiple-choice exercises. This was accomplished by creating a ReactJS component called `drop`, which takes "word" and "choices" as props. Bootstrap was used to implement the dropdown functionality, and React's `useState` hook was employed to dynamically change the appearance of buttons based on user responses.

4. **Script for Passage Transformation:** A Python script was written to take a passage as input, split it into words, and create a serialized dictionary containing these words. A for loop was then used to iterate a number of times equal to 70% of the total number of words in the passage. In each iteration, a key value was generated by adding a randomly generated number between 2 and 7. Using Morfeusz2, word forms were generated, and if at least 2 word forms were successfully generated, the BeautifulSoup library was used to add the necessary tags for the `drop` component, along with the required props. Finally, the dictionary was converted back into a paragraph, and a POST request was made to the backend at the `/passages` endpoint to add the passages.

5. **Backend Development:** A Django model was created to represent passages, and Django Rest Framework's Model Serializer class, generic class-based views, and API views were used to quickly set up the API for CRUD operations. Additionally, a custom permission class was implemented to restrict editing and deletion of passage objects to their respective owners.

## Frontend Design

The frontend design of the application was also a significant focus. The `useEffect` hook was utilized to fetch data asynchronously from a JSON file when the component mounts. The fetched data was then shuffled and stored in the `passages` state. A loop was used to wrap each paragraph in a `div` element, and React-Jsx-Parser was employed to dynamically render the parsed passages. Careful attention was paid to ensure responsiveness across different screens.

Feel free to explore the codebase and contribute to the project!
