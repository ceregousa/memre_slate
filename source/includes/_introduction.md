# Introduction

Welcome to the Memre API! You can use this API to add Memre's patented learning science technologies into your own product.

### Example use case

As an example, let's say you have an app that teaches users various software development concepts. At the end of each lesson the user is quizzed on the concepts they've learned. You can use the Memre API to help the user learn these concepts most effectively. You can also use the API to get various statistics about the user's knowledge. Additionally, you will be able to get various statistics about the concepts themselves (eg relative difficulty).

### High-level overview

At a high-level, this API works by your app telling us every time a user is quizzed on a concept and whether they got it correct or not. Our learning engine takes that info into account, as well as other users' results on each concept to calculate various things useful for optimizing learning.

In order to tell us a certain user's results on a certain concept, our system needs to have corresponding records for each user and each concept. See the [Creating a User](#creating-a-user) and [Importing Content](#importing-content) sections for details, but essentially, you would create records for each user and each concept and save the returned IDs in your database for future API calls.

### General API Notes

Our API follows the [JSON API](http://jsonapi.org/) standard. All endpoints follow standard RESTful practices and start with the URL `https://partners.cerego.com/v3/`. Most endpoints will require you to pass in your partner account ID. This is a value which we will provide you.
