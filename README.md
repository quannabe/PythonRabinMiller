PythonRabinMiller
=================

####A Python implementation of the Rabin-Miller (or, Miller-Rabin) method to probabilistically test primality

Read more here: http://en.wikipedia.org/wiki/Miller%E2%80%93Rabin_primality_test

##Accuracy
If a number is composite, Rabin-Miller has been shown to return composite 3/4 of the time.

This method may give **False Negatives** returning prime when the number is composite-- but will not return **False Positives** returning composite when the number is prime.

Running this method for many iterations will greatly improve the accuracy. So, if we run the test for m iterations, we see that our probability of being incorrect is: **(3/4)^m**

**Keep in mind**-- we only need a single witness to be found in order for us to be able to classify the number as composite-- as soon as we find this witness, we can stop looking.

##Example

n is the number we are testing for primality
a is some random base where: 0 <= a <= n-1

This method will return '1' if suspected prime, and the witness otherwise


First, let us check a very large prime: **35742549198872617291353508656626642567**

`n =  35742549198872617291353508656626642567`

`a = randint(0,n-2)`

`print rabMill(a,  n-1, n)`

At each iteration, the method will return 1

Now, let us try a composite number-- which happens to be a **Carmichael Number**: **294409**

`n =  294409`

`a = randint(0,n-2)`

`print rabMill(a,  n-1, n)`

Output:

`reject, witness:  72180`

Here, I was able to find a winess in a single iteration (your witness may vary)

This method seems to be quite efficient. For example, when running the Rabin-Miller method 1,000,000 times on the above Carmichael Number, using a random ‘a’ value (from 0 to n-2) I found that ‘Composite’ was returned 0.9257% of the time-- quite better than the worst case of 0.75!





