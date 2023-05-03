Download Link: https://assignmentchef.com/product/solved-cs1675-homework9-bayes-net-written-exercises
<br>
<u>Part I: Bayes net written exercises</u>

Enter your responses in a file <span style="font-family: courier new;">report.pdf/docx</span> .

<ol type="1">

 <li>Bishop Exercise 8.11</li>

 <li> In this exercise, we’ll do some cross-domain recommendation, where we assume that there is a correlation between a user’s taste in music and film. We’ll only consider one music genre, namely jazz (which we’ll denote by <span style="font-family: courier new;">J</span>), and four films, “Waking Life” (denoted by <span style="font-family: courier new;">W</span>), “Borat” (denoted by <span style="font-family: courier new;">B</span>), “Cinema Paradiso” (denoted by <span style="font-family: courier new;">C</span>) and “Requiem for a Dream” (denoted by <span style="font-family: courier new;">R</span>). We’ll assume that conditioned on whether the user likes jazz, the movie likes/dislikes are independent. The prior probability of liking jazz is 30%. We’ve defined the following (combined) conditional probability table, where “=1” means “likes”. We are conditioning on the first column.

  <table border="1">

   <tbody>

    <tr>

     <td><span style="font-family: courier new;">J=1</span></td>

     <td><span style="font-family: courier new;">W=1</span></td>

     <td><span style="font-family: courier new;">B=1</span></td>

     <td><span style="font-family: courier new;">C=1</span></td>

     <td><span style="font-family: courier new;">R=1</span></td>

    </tr>

    <tr>

     <td>T</td>

     <td>80</td>

     <td>20</td>

     <td>70</td>

     <td>50</td>

    </tr>

    <tr>

     <td>F</td>

     <td>30</td>

     <td>50</td>

     <td>30</td>

     <td>40</td>

    </tr>

   </tbody>

  </table>

  <ol type="a">

   <li>What is the probability the user likes jazz, given that she likes the first and fourth movies but dislikes the second and third?</li>

   <li>How about the probability that the user likes jazz, given that she likes all the movies?</li>

  </ol></li>

</ol>

<u>Part II: HMM naive solution</u>

In the remainder of this assignment, you will implement a basic Hidden Markov model. We’ll use the HMM from our in-class part-of-speech tagging example, whose states are <span style="font-family: courier new;">PropNoun, Noun, Verb, Det</span>. The transition probabilities are the same as in the example shown in class. The observation probabilities are defined as follows, and are defined in the provided file <span style="font-family: courier new;"><a href="https://people.cs.pitt.edu/~kovashka/cs1675_fa18/hmm_starter.m">hmm_starter.m</a></span>.

<table border="1">

 <tbody>

  <tr>

   <td>State/Observation</td>

   <td>john</td>

   <td>mary</td>

   <td>cat</td>

   <td>saw</td>

   <td>ate</td>

   <td>a</td>

   <td>the</td>

  </tr>

  <tr>

   <td><span style="font-family: courier new;">PropNoun</span></td>

   <td>0.40</td>

   <td>0.40</td>

   <td>0.10</td>

   <td>0.01</td>

   <td>0.05</td>

   <td>0.03</td>

   <td>0.01</td>

  </tr>

  <tr>

   <td><span style="font-family: courier new;">Noun</span></td>

   <td>0.25</td>

   <td>0.05</td>

   <td>0.30</td>

   <td>0.25</td>

   <td>0.05</td>

   <td>0.05</td>

   <td>0.05</td>

  </tr>

  <tr>

   <td><span style="font-family: courier new;">Verb</span></td>

   <td>0.04</td>

   <td>0.05</td>

   <td>0.04</td>

   <td>0.45</td>

   <td>0.40</td>

   <td>0.01</td>

   <td>0.01</td>

  </tr>

  <tr>

   <td><span style="font-family: courier new;">Det</span></td>

   <td>0.01</td>

   <td>0.01</td>

   <td>0.01</td>

   <td>0.01</td>

   <td>0.01</td>

   <td>0.45</td>

   <td>0.50</td>

  </tr>

 </tbody>

</table>

In a function <span style="font-family: courier new;">naive_solution.m</span>, write code to compute the probability of observing each of the following sentences, using the naive solution. You can map each word to a number that is its index into our vocabulary (the union of the column headers above, except the first one), then a sentence is just a vector of numbers; see Part <span style="color: red;">III</span> for an example. Use the provided <span style="font-family: courier new;"><a href="https://people.cs.pitt.edu/~kovashka/cs1675_fa18/permn.zip">permn.zip</a></span> to compute combinations with replacement, to get your list of possible state sequences.

<b>Inputs:</b>

<ul>

 <li>the transition matrix <span style="font-family: courier new;">A</span> (from <span style="font-family: courier new;">hmm_starter.m</span>),</li>

 <li>the observation matrix <span style="font-family: courier new;">B</span> (from <span style="font-family: courier new;">hmm_starter.m</span>),</li>

 <li><span style="font-family: courier new;">N</span>, the number of states,</li>

 <li><span style="font-family: courier new;">M</span>, the number of words in the vocabulary, and</li>

 <li>a vector of integers <span style="font-family: courier new;">sent</span> representing the sentence whose observation probability we want to compute.</li>

</ul>

<b>Outputs:</b>

<ul>

 <li><span style="font-family: courier new;">prob</span>, the probability of observing the input sentence.</li>

</ul>

<u>Part III: Testing HMM on part-of-speech tagging</u>

Finally, in a script <span style="font-family: courier new;">hmm_demo.m</span>, pick five of the sentences below, and compute their probability of occurrence. In a file <span style="font-family: courier new;">report.pdf/docx</span>, discuss what you observe about which of them seem more likely than others, and whether what you observe makes sense.

<ul>

 <li>“john saw the cat.” (or using our mapping to numbers, <span style="font-family: courier new;">sent = [1 4 7 3];</span>)</li>

 <li>“john ate.”</li>

 <li>“john saw mary.”</li>

 <li>“mary saw john.”</li>

 <li>“cat saw the john.”</li>

 <li>“john saw the saw.”</li>

 <li>“john ate the cat.”</li>

</ul>

<b>Submission:</b> Please include the following files:

<ul>

 <li><span style="font-family: courier new;">report.pdf/docx</span></li>

 <li><span style="font-family: courier new;">naive_solution.m</span></li>

 <li><span style="font-family: courier new;">hmm_demo.m</span></li>

</ul>