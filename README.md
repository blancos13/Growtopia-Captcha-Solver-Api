
# Growtopia-Captcha-Solver

Varlist

Example Solver In C++
```c++
        case fnv32("onShowCaptcha"): {
        gt::send_log("`9Solving Captcha...");
        auto menu = varlist[1].get_string();
        auto g = split(menu, "|");
        std::string captchaid = g[1];
        std::string captchaid2 = g[2];
        std::string captchaid3 = g[3];
        std::string url = "ubistatic-a.akamaihd.net/0098/captcha/generated/";
        utils::replace(captchaid, "0098/captcha/generated/", "");
        utils::replace(captchaid, "PuzzleWithMissingPiece.rttex", "");
        captchaid = captchaid.substr(0, captchaid.size() - 1);
        cout << captchaid << endl;
        cout << captchaid2 << endl;
        cout << captchaid3 << endl;
        std::this_thread::sleep_for(std::chrono::milliseconds(1000));
        http::Request request{ "http://54.36.0.86/captcha=" + captchaid };
        const auto responses = request.send("GET");
         std::string output = std::string{ responses.body.begin(), responses.body.end() };
        g_server->send(false, "action|dialog_return\ndialog_name|puzzle_captcha_submit\ncaptcha_answer|" + output + "|CaptchaID|" + g[4]);
       gt::send_log("`cSolved Captcha As `9" + output);
        return true;//success
    } break;
```

### Api
http://54.36.0.86/captcha=[CaptchaUID]
http://54.36.0.86/captcha=d70be9c4-d8d7-4355-bac4-0384baf6d216


### Information
Solve Time 0-1.2 Seconds.<br>

### Example Request
Request Method : GET

```curl "http://54.36.0.86/captcha=d70be9c4-d8d7-4355-bac4-0384baf6d216 ```
### Response
Response txt format
```txt
0.29571
```
