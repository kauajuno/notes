# Debugging with Profiler

Remember that debug bundle we installed way earlier on this guide? Time to make good use of it. Debugging APIs might be hard some time.

Actually, debug itself is not a bundle, but an alias for installing a package with 3 bundles:

- symfony/monolog-bundle
- symfony/debug-bundle
- symfony/web-profiler-bundle

More on the first two later, let's focus on the web profiler bundle. It gives you detailed profiling of requests, database queries and other amazing features. Consider it essential to the development routine.

After sending a request, you'll notice that an icon with two arrows (one going each way) is going to appear on your toolbar. Click on it and you'll see the requests you've sent.

Alternatively you can go to `localhost/_profiler` to go to the web profiler home page where you can monitor all of you requests and access their data anyway.
