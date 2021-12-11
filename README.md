# What is lcurl? ![CI](https://github.com/nickjj/lcurl/workflows/CI/badge.svg?branch=master)

It's a Bash script (yep it uses Bash features) that runs a specific curl
command X number of times in a loop. It will report back the HTTP status code,
how long it took to get a response, a timestamp and the loop count.

Here's an example of visiting <https://example.com> every 250ms for a max of 5
times:

```sh
lcurl https://example.com 0.25 5
```

Running the above command will produce this output:

```sh
200 | 0.069927s | 2021-12-11T08:47:00 | 1/5
200 | 0.063947s | 2021-12-11T08:47:00 | 2/5
200 | 0.060945s | 2021-12-11T08:47:01 | 3/5
200 | 0.068982s | 2021-12-11T08:47:01 | 4/5
200 | 0.066179s | 2021-12-11T08:47:01 | 5/5
```

If you omit the max number of times it will run `999999` times by default. The
URL and delay (in seconds) are required.

## Installation

Since this script uses curl you'll need to have `curl` installed beforehand.
It's available with most package managers depending on your OS. For example you
can apt, brew, pacman or yum install curl.

Then all you have to do is download this `lcurl` script, make sure it's
executable and place it somewhere on your system path.

#### 1 liner to get `lcurl` downloaded to `/usr/local/bin`:

```sh
sudo curl \
  -L https://raw.githubusercontent.com/nickjj/lcurl/0.1.0/lcurl \
  -o /usr/local/bin/lcurl && sudo chmod +x /usr/local/bin/lcurl
```

That will download the latest release. If you want to download the bleeding
edge version you can replace the *version number* with *main* in the above
command.

Confirm it works by running `lcurl`. You should be greeted with a help menu
that shows an example on how to use it.

## FAQ

### When would you use this script?

This could be useful to help make sure you're able to perform zero down time
deployments of your application. As you roll-out a new version of your app you
can use this script to hit your site to make sure it always responds back with
200s.  That's the exact use case of why I created this script but I'm sure
there's other use cases that you can use this for too.

### When wouldn't you use this script?

If you want to get high precision benchmarks or are profiling an application
there are much better tools for this such as [wrk](https://github.com/wg/wrk).
`lcurl` reports back how long it took to receive a response but that's mainly
because "why not". It's nice to have and it took about a minute to implement
because it's a value that's provided by curl.

### Why did you name the script `lcurl` and not `curll`?

I didn't want TAB completing `curl` to give you the option of running this
script because let's be real now, most of the time if you type out `cur` your
intent is to run `curl` not this script.

## About the Author

I'm a self taught developer and have been freelancing for the last ~20 years.
You can read about everything I've learned along the way on my site at
[https://nickjanetakis.com](https://nickjanetakis.com/). There's hundreds of
[blog posts](https://nickjanetakis.com/blog/) and a couple of [video
courses](https://nickjanetakis.com/courses/) on web development and deployment
topics. I also have a [podcast](https://runninginproduction.com) where I talk
to folks about running web apps in production.
