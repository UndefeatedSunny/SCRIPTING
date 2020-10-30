
## Check The ScreenShot

        Explanation
That's because these backslashes have separate behaviours when used with both commands.

For echo, these backslashes are treated as meta character having properties that suppress the powers of the following character.

In case of paste command,
If you see its manual, it's mentioned if \\ are used, it represents a backslash character.

Now, generally, delimiters are given in ' ' (strong quotes) that's why you may see the expected results in that case.

With weak quotes ("")  the results are unspecified.


Or we can understand it like this:

Inside weak quotes,
"\\" will represent "\" (since paste translates \\ to \) and then it will undergo another translation because of the weak quotes 
that's why you see an error of unescaped backslash.

While in strong quotes, '\\' will translate to a single backslash (single translation only)

Therefore, to be able to use \ as delimiter in weak quotes,

We have to specify: "\\\\"
Now, first translation: "\\" and then second translation will yield a single backslash.
