The API isn't commonly discussed, as it is quite elusive to most marketers who don't spend a lot of time programming. Marketers market, programmers program, but few cross domains from one to the other. I'm here to bridge the gap between the two disciplines, which will inevitably happen as business become more tech centric and demand more out of their marketing teams. Therefore, I will attempt to explain the API an in easy to understand format that anyone can start using to their benefit.

Documentation

Eloqua Dev Help Center \(Old\) [http://docs.oracle.com/cloud/latest/marketingcs\_gs/OMCAB/](http://docs.oracle.com/cloud/latest/marketingcs_gs/OMCAB/)

REST API \(Latest\) [http://docs.oracle.com/cloud/latest/marketingcs\_gs/OMCAC/](http://docs.oracle.com/cloud/latest/marketingcs_gs/OMCAC/)

What is an API?

What is a REST API?

What are the HTTP Responses?

What is a HTTP Header?

What is a Bulk API?

What is Swagger?

Wow, this stuff is confusing

Yeah, it is. Because there are really no formal specifications around what an API is, it makes things difficult. Although there is a lot to know within this domain, and plenty of abstract concepts to the end user, everything you need to know should be right here.

Getting Started

What you will need:

* Login credentials granted the necessary rights \(Marketing Users - Advanced permission\)
* Your "Company" site name
* Postman

Determining your Basic Authentication Header

Basic Authentication is the quickest way to get started with the API. It's not as preferred as Oauth, but it is fine to begin with. Once you have your Authentication Header, save it, as you will need it to determine your base url and to perform your API calls.

1. Write down your Company/Instance \(the first field on the Eloqua login page, yes this is case sensitive\), your username \(usually First.Last\), and your password.
2. Then, put them together but with a backslash `\` between the Company and username, and a colon `:` between the username and password. You end up with `Acme\John.Doe:secret1`.
3. Base64 the concatenation you previously created. This can be done [online](http://www.motobit.com/util/base64-decoder-encoder.asp), or through a simple BASH command \(through Cygwin or WSL on Windows, or Terminal on OSX\) using the base64 built-in. If using BASH, use the printf utility[^1] and pipe it to base64, and be mindful of escaping your backslash. For example, `printf Acme\\John.Doe:secret1 | base64`. Copy that output and save it somewhere, this is your authentication header. For our example, the output would be `QWNtZVxKb2huLkRvZTpzZWNyZXQx`. You can verify this by decoding it, using `base64 -d <<< QWNtZVxKb2huLkRvZTpzZWNyZXQx` .

Determine your Base URL

[^1]: echo doesn't work in this case because it adds a newline to its output. You can prove this by emulating the same result using `printf '%s\n' 'something'` and compare it to `echo something`.

