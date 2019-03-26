# Hacking_notes_ppt1_Iman_and_Shannon

**Password Hash Recovery**

**Iman and Shannon**

**Introduction**

The ideal password is something you know, something that a computer can verify
you that using it, and something unguessable, even with internet resources
access. We will prove that it is difficult to come close to this ideal in
practice. Surely, you use passwords in your daily life, and you are familiar
with it. There is no possible way to have computer without using many passwords.
Many things act as passwords, such as the ATM PIN number which is equivalent to
a password. Even in case you forget your password, a website will try to verify
you based on the things that you should know which are finally acting as
passwords like your social security number, your mother’s maiden name, or your
date of birth. An obvious problem is that these things are not secret. We’ll see
that, when users select passwords, they tend to select bad passwords, which
makes password “cracking” surprisingly easy. In fact, we’ll provide some basic
mathematical arguments to show that it’s inherently difficult to achieve
security via passwords. One solution to the password problem would be to use
randomly generated cryptographic keys in place of passwords. Then the work of
cracking a password would be equivalent to the work of a brute force exhaustive
key search. The problem with such an approach is that humans must remember their
passwords. But we’re getting ahead of ourselves. First, we need to understand
why passwords are so popular. That is, why is “something you know” more popular
than “something you have” and “something you are,” when the latter two are,
presumably, more secure? The answer is, primarily, cost,1 and secondarily,
convenience. Passwords are free, while smartcards and biometric devices cost
money. Also, it’s more convenient for an overworked system administrator to
issue a new password than to provide and configure a new smartcard. And, of
course, it’s much more convenient to reset a compromised password than to issue
a user a new thumb.

**HOW TO CRACK A PASSWORD**
---------------------------

Password cracking or ‘password hacking’ as is it more commonly referred to is a
cornerstone of Cybersecurity and security in general.

Password hacking software has evolved tremendously over the last few years but
essentially it comes down to several thing: firstly, what systems are in place
to prevent certain popular types of password cracking techniques (for example
‘captcha forms’ for brute force attacks), and secondly, what is the computing
processing power of the hacker?

Typically, password hacking involves a hacker brute forcing their way into a
website admin panel (or login page for example) and bombarding the server with
millions of variations to enter the system. That requires CPU. The faster the
machine the faster the cracking process will be. Yes, a ‘clued-up’ Cybersecurity
Professional will be able to prevent brute forcing but you’ll be amazed at the
number of vulnerable websites that can be forced into with the password hacking
software that we’ve listed below.


![image](https://user-images.githubusercontent.com/48844366/54868627-a6553a00-4d4b-11e9-9225-8abfa67774fd.png)

**THE CAST OF CHARACTERS**

Following tradition, Alice and Bob are the good guys. Occasionally we’ll require
additional good guys, such as Charlie. Trudy is a generic bad guy who is trying
to attack the system in some way. Some authors employ a team of bad guys where
the name implies the particular nefarious activity. In this usage, Trudy is an
“intruder” and Eve is an “eavesdropper” and so on. Trudy will be our all-purpose
bad guy. Alice, Bob, Trudy and the rest of the gang need not be humans. For
example, one possible scenario would be that Alice is a laptop, Bob a server,
and Trudy a human.

**Math of Password Cracking**

Now we’ll take a closer look at the mathematics behind password cracking. In
this section, we’ll assume that all passwords are eight characters in length and
that there are 128 choices for each character, resulting in

1288 = 256

possible passwords. We’ll also assume that passwords are stored in a password
file that contains 210 hashed passwords, and that Trudy has a dictionary of 220
common passwords. From experience, Trudy expects that any given password will
appear in her dictionary with a probability of about 1/4. Also, “work” is
measured by the number of hashes computed. In particular, comparisons are free.
Under these assumptions, we’ll determine the probability of success in each of
the following four cases.

I. Trudy wants to find Alice’s password (perhaps Alice is the administrator)
without using the dictionary of likely passwords.

II. Trudy wants to find Alice’s password using the dictionary.

III. Trudy wants to find any password in the hashed password file, without using
the dictionary.

IV. Trudy wants to find any password in the hashed password file, using the
Dictionary. In each of these cases, we’ll consider both salted and unsalted
password files.

• Case I: Trudy decides that she wants to find Alice’s password. Trudy, who is
somewhat absent-minded, has forgotten that she has a password dictionary
available. In this case, Trudy has no choice but to try all passwords until she
happens to come across the correct password. This is precisely equivalent to an
exhaustive key search and the expected work is

256/2 = 255.

The result here is the same whether the passwords are salted or not, unless— in
the unsalted case—Trudy can precompute and store the hashes of all possible
passwords. This is a great deal of work, and we’ll assume that it is beyond
Trudy’s capability.

• Case II: Trudy again wants to recover Alice’s password, but she is going to
use her dictionary of common passwords. With probability 1/4, Alice’s password
will appear in the dictionary, in which case Trudy would expect to find it after
hashing half of the words in the dictionary, that is, after 219 tries. With
probability ¾ the password is not in the dictionary, in which case Trudy would
expect to find it after about 255 tries. Then the expected work is

![](media/c7703aeb2951cef2f09df5bc06b00def.png)

The expected work is almost the same as in the previous case, where Trudy did
not use her dictionary. However, in practice, Trudy could simply try all in
words in her dictionary and quit if she did not find Alice’s password. Then the
work would be at most 220 and the probability of success would be 1/4. If the
passwords are unsalted, Trudy could precompute the hashes of all 220 password in
her dictionary. Then ignoring the one-time work of computing the dictionary
hashes, the term involving 219 would vanish from the calculation above.

• Case III: In this case, Trudy will be satisfied to find any one of the 1024
passwords in the hashed password file. Trudy has again forgotten about her
dictionary. Let y0, y1, . . . , y1023 be the password hashes.We’ll assume that
all 210 passwords in the file are distinct. Let p0, p1, . . . , p256−1 be a list
of all 256 possible passwords. Trudy needs to make 255 distinct comparisons
before she expects to find a match. If the passwords are not salted, then Trudy
computes h(p0) and compares it with each yi , for i = 0, 1, 2, . . . , 1023.
Next she computes h(p1) and compares it with all yi and so on. Then each hash
computation provides Trudy with 210 comparisons with hashed passwords. Since
work is measured only in terms of hashes, the expected work is

255/210 = 245.

On the other hand, if the passwords are salted, denote the salt value for yi as
si . Then Trudy computes h(p0, s0) and compares it with y0. Next, she computes
h(p0, s1) and compares it with y1 and she continues in this manner up to h(p0,
s1023). Then Trudy must repeat this entire process with password p1 and then
with password p2 and so on. In this case, each hash computation only yields one
usable comparison and consequently the expected work is 255, which is the same
as in Case I, above.

• Case IV: Finally, suppose that Trudy wants to find any one of the 1024
passwords in the hashed password file, and she will make use of her dictionary.
The probability that at least one password is in dictionary is

![](media/7dc86412a2cce447975c6a95873b08a8.png)

so we can safely ignore the case where no password in the file appears in
Trudy’s dictionary. If the passwords are not salted, then, since we are assuming
at least one of the passwords is in the dictionary, Trudy only needs to make
about 219 comparisons before she expects to find a password. As in Case III,
each hash computation yields 210 comparisons, so the expected work is about

219/210 = 29.

In the salted case, let y0, y1, . . . , y1023 be the password hashes and let s0,
s1, . . . , s1023 be the corresponding salt values. Also, let d0, d1, . . . ,
d220−1 be the dictionary words. Suppose that Trudy first computes h(d0, s0) and
compares it to y0, then she compute h(d1, s0) and compares it to y0 and so on.
That is, Trudy first compares y0 to all of her (hashed) dictionary words. Then
she compares y1 to all of her dictionary words and so on. If y0 is in the
dictionary (which has probability 1/4), Trudy can expect to find it after about
219 hashes, and if it is not in the dictionary (which has probability 3/4) Trudy
will compute 220 hashes. If Trudy finds y0 in the dictionary then she’s done. If
not, Trudy will have computed 220 hashes before she moves on to y1. Continuing,
in this manner we find that the expected work is about

![](media/d9c91df5c076258fd6d6649ca5cd338f.png)

This calculation shows the tremendous impact of a relatively small dictionary
that has a reasonable chance of containing a password, together with a password
file of a reasonable size. Salting doesn’t help too much here as the work is
(roughly) bounded by the size of the dictionary. Also note that the result is
the same regardless of the number of possible passwords, provided all other
assumptions remain Unchanged. The bottom line is that password cracking is too
easy, particularly in situations where one weak password may be sufficient to
break the security of an entire system—which is often the case. In password
cracking, the numbers strongly favor the bad guys.

**Hashcat Tool:**

Hashcat is the self-proclaimed world's fastest [password
recovery](https://en.wikipedia.org/wiki/Password_cracking) tool. It had a
proprietary code base until 2015 but is now released as free software. Versions
are available for Linux, OS X, and Windows and can come in CPU-based or
GPU-based variants. Examples of hashcat-supported hashing algorithms are
Microsoft [LM hashes](https://en.wikipedia.org/wiki/LM_hash),
[MD4](https://en.wikipedia.org/wiki/MD4),
[MD5](https://en.wikipedia.org/wiki/MD5),
[SHA-family](https://en.wikipedia.org/wiki/SHA1), [Unix
Crypt](https://en.wikipedia.org/wiki/Crypt_(Unix)) formats, MySQL, and Cisco
PIX.

Hashcat has made its way into the news many times for the optimizations and
flaws discovered by its creator, which were exploited in subsequent hashcat
releases. (For example, the flaw in
[1Password](https://en.wikipedia.org/wiki/1Password)'s password manager hashing
scheme.

**Hashcat Features**


![image](https://user-images.githubusercontent.com/48844366/54868639-dac8f600-4d4b-11e9-8ea9-19bd9bf8bfd9.png)

**Screenshot**

![image](https://user-images.githubusercontent.com/48844366/54868701-9c800680-4d4c-11e9-817a-8825b9e65d6f.png)

**Hahscat Arguments**


![image](https://user-images.githubusercontent.com/48844366/54868709-b0c40380-4d4c-11e9-8bf1-ca155222c135.png)

**Pattern-Based Filters**

>   A filter pattern provides the ability to select a set of criteria that
>   represents a specific behaviour.

>   The grep command can be used to search for certain patterns in files. An
>   example is shown below:

![image](https://user-images.githubusercontent.com/48844366/54868787-80309980-4d4d-11e9-941f-c4262de93f9f.png)

One of the uses in a pattern-based filter is to block a “denial of service
attack”. A program can be used to monitor for certain patterns in files before
the information reaches a server and thus block the file.

**GNU Optimization**

**Background**

GNU is an acronym for General Public License Not Unix. It was developed by
Richard Stallman who started the software development around the late 1980’s. It
is open-source and contains components such as the GNU Compiler Collection
(GCC), debugging (GDB), command line tools (e.g. grep, cat) and a text editor
(e.g. vim). It interacts with many kernels including Linux .

One of the options in the GCC is the optimization option. Optimization is used
to improve the performance of the executable, the performance of compilation
time and/or the size of the program.

**What does it do?**

The compiler attempts to group together the same variable, function etc. before
it is translated into assembler language. Each optimization level has a group of
flags that are turned on. There is also the ability to use an optimization level
and omit certain flags. An example of some of the option flags that are turned
on for optimization of debug is shown below:

An example of viewing the flags that are turned on for debugging optimization is
shown below.

![image](https://user-images.githubusercontent.com/48844366/54868798-b110ce80-4d4d-11e9-924e-91789d4ce95b.png)

![image](https://user-images.githubusercontent.com/48844366/54868820-e1586d00-4d4d-11e9-94b1-004099169915.png)

**Why is it used?**

An optimization for performance becomes more important in production
environments as production costs increase. Typically, a production environment
would use optimization level of 2 (-O2). Optimization of size (-Os) becomes more
important if the time for downloading patches or applications is important. For
example, in a production environment, the time for downloading in a production
needs to be minimized. It should also be noted that when optimization is used,
it increases compilation time. Also, a hacker can take advantage of optimization
levels, for example, to improve download speed (-Os) or improve debugging.

**Optimization Levels**

Each level of optimization attempts to prioritize either performance or size.

Listed below are the options and the objectives of each:

\-O0 turns off the optimizations that are running in the system. Fastest
compilation speed and is good for debugging.

\-O1 the compiler attempts to reduce compiler time without impacting the
performance or size.

\-O2 the code is fully optimized with the goal of improving performance. It
includes all the flags of level 1 and additional flags.

\-O3 includes all the flags of level 2 and additional flags. It attempts to
improve performance of inline programs. It has been noted (Khem Raj, GCC/Clang
Optimizations for Embedded Linux), that this level may not improve performance
better than level 2 because it is quite dependent on how inlining is handled in
the code.

–Og the goal is to improve the debugging experience greater than when all
optimizations are turned off (-O0).

The more efficiently the code is written, the greater the improvement in
performance, and /or reduction of size when using the optimization options.

**References**

>   **Hashcat**

-   <https://hashcat.net/hashcat/>

-   <https://www.youtube.com/watch?v=EfqJCKWtGiU>

-   A. A. Putri Ratna, P. Dewi Purnamasari, A. Shaugi and M. Salman, "Analysis
    and comparison of MD5 and SHA-1 algorithm implementation in Simple-O
    authentication based security system," *2013 International Conference on
    QiR*, Yogyakarta, 2013, pp. 99-104. doi: 10.1109/QiR.2013.6632545.

-   C. Ge *et al*., "Optimized Password Recovery for SHA-512 on GPUs," *2017
    IEEE International Conference on Computational Science and Engineering (CSE)
    and IEEE International Conference on Embedded and Ubiquitous Computing
    (EUC)*, Guangzhou, 2017, pp. 226-229. doi: 10.1109/CSE-EUC.2017.226.

-   Y. Liu *et al*., "GENPass: A General Deep Learning Model for Password
    Guessing with PCFG Rules and Adversarial Generation," *2018 IEEE
    International Conference on Communications (ICC)*, Kansas City, MO, 2018,
    pp. 1-6. doi: 10.1109/ICC.2018.8422243

-   M. Stamp, *Information Security: Principles and Practice.* Hoboken, N.J:
    Wiley-Interscience, 2006.

-   https://www.concise-courses.com/hacking-tools/password-crackers/

**Pattern based filters**

-   <https://docs.oracle.com/cd/E19455-01/806-2902/6jc3b36dn/index.html>

-   <https://ieeexplore.ieee.org/document/6994276>

**GNU Optimization**

-   <https://en.wikipedia.org/wiki/GNU>

-   <https://gcc.gnu.org/onlinedocs/gnat_ugn/Optimization-Levels.html>

-   <https://gcc.gnu.org/onlinedocs/gcc/Optimize-Options.html>

-   <https://youtu.be/jVYnT_onb70?t=4>

-   <https://www.ibm.com/support/knowledgecenter/en/ssw_aix_72/com.ibm.aix.performance/comp_opt.htm>
