### Steps

1. Initialize new project `composer composer create-project sulu/skeleton my-project -n`
2. Add translation `bin/console sulu:admin:download-language`
3. Create database and initialize `bin/adminconsole sulu:build dev`
4. Download the elasticsearch version that matches your installation's (7.17 in my case) `composer require "elasticsearch/elasticsearch:7.17.*"`
5. Download the article bundle (latest) `composer require sulu/article-bundle`
6. Download elasticsearch bundle `composer require "handcraftedinthealps/elasticsearch-bundle:^5.2"`
7. (optionnal) Modify `ELASTICSEARCH_INDEX` value in your `.env` file
8. Create elasticsearch indexes
```
php bin/console ongr:es:index:create
php bin/console ongr:es:index:create --manager=live
```
9. Activate all your articles rights in your User settings `Settings > User roles > your role`
10. Create a smart content in your `homepage.xml`
11. Render your smart content in your `homepage.html.twig`
12. Create a user role `php bin/console sulu:security:role:create` and assign it the `website` system
13. Create a new user either in your admin or `php bin/console sulu:security:role:create`
14. Uncomment the routes `login` and `logout` in your `config/routes_website.yaml`
15. Uncomment your `website` firewall in your `security.yaml`
16. Create your own login page `https://github.com/sulu/sulu/blob/2.x/templates/static/login.html.twig`
17. Go to your /login page and connect as a user (that you created on point 13)

You should be redirected to the frontpage where the smart content is, and have the following error:
![{"error":{"root_cause":[{"type":"parsing_exception","reason":"[term] query does not support [type]","line":1,"col":183}],"type":"x_content_parse_exception","reason":"[1:183] [bool] failed to parse field [must]","caused_by":{"type":"x_content_parse_exception","reason":"[1:183] [bool] failed to parse field [should]","caused_by":{"type":"parsing_exception","reason":"[term] query does not support [type]","line":1,"col":183}}},"status":400}](images/error.png)

The error appears if:
- You try to use smart content with a user connected via Sulu Community Bundle
- If you connect as a sulu User where a smart content is active
