### i18n Dictionary
The following file `zh-CN.yml` should be under config/locale in order for i18n to locate it.
```ruby
zh-CN:
  rewards: "积分"
  redeem: "兑换"
  view_count: "观看"
  likes: "赞"
  favorite: "收藏"
  layouts:
    header:
      READSS: "网站中文名"    
      log_out: "退出"
      log_in: "登录"
  videos:
    index:
      Videos: "所有视频"
    redeem:
      redeem_success: "视频 %{title} 现在可以观看。"
      redeem_failure: "您的积分不够兑换视频。"
  videos_helper:
    redeem_confirm: "观看 %{title} 将花费一个积分，您现有%{rewards}个积分。"
    redeem_verify: "请问观看视频后您还有多少积分？"
    show_link:
      show: "观看视频"
```
Several choices of dictionary entries are illustrated here:
* variable: access by string or symbol directly, such as `t(:rewards)` or `t('redeem')`. These are the top level entry without any structure.
* For other variables in a hierachy, it can be accessed by an absolute path or a relative path:
  * absolute path: `t('videos_helper.show_link.show')` is probably associated with `show_link` method closely. `t('videos_helper.redeem_verify')`
                   is probably used across the videos_helper module. One can organize it in different ways, as long as it is accessed in absolute
                   path.
  * relative path: `t('.redeem_success')` can only be accessed in the view or controller associated with videos#redeem. Note the dot. That 
                  is why it's called a relative path. The same holds for `t('.READSS')` which is only available in _header.html.erb. Again,
                  relative lookup only works in view or controller which often share the same name as the corresponding action.
