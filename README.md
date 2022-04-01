# You can use Flashbar just creating builder as mention below

```
enum class SnackBarType{
    ERROR,SUCCESS,MESSAGE
}

fun String.showSnackBar(context: Activity?, snackBarType:SnackBarType = SnackBarType.ERROR, duration: Long = 4000, @DrawableRes iconId: Int? = 0, title: String? = "") {
    if (context != null) {
        var color = android.R.color.holo_red_light
        var textColor = R.color.white
        when (snackBarType) {
            SnackBarType.ERROR -> {
                textColor = R.color.white
            }
            SnackBarType.SUCCESS -> {
                color = android.R.color.holo_green_light
                textColor = R.color.white
            }
            SnackBarType.MESSAGE -> {
                textColor = R.color.white
            }
        }

        val builder = Flashbar.Builder(context)
            .gravity(Flashbar.Gravity.TOP)
            .title(context.getString(R.string.app_name))
            .titleTypeface(ResourcesCompat.getFont(context, R.font.roboto_medium)!!)
            .titleSizeInPx(context.resources.getDimension(R.dimen._14ssp))
            .titleColorRes(textColor)
            .message(this)
            .messageColorRes(textColor)
            .messageTypeface(ResourcesCompat.getFont(context, R.font.roboto_medium)!!)
            .messageSizeInPx(context.resources.getDimension(R.dimen._12ssp))
            .backgroundColorRes(color)
            .enableSwipeToDismiss()
            .duration(duration)
            .enterAnimation(
                FlashAnim.with(context)
                    .animateBar()
                    .duration(750)
                    .alpha()
                    .overshoot()
            )
            .exitAnimation(
                FlashAnim.with(context)
                    .animateBar()
                    .duration(400)
                    .accelerateDecelerate()
            )

        if (iconId != null && iconId != 0) {
            builder.icon(iconId)
        }

        if (title?.isNotBlank() == true) {
            builder.title("\n\n" + title)
        }

        val flashbar = builder.build()
        if (!(flashbar.isShowing() || flashbar.isShown())) {
            flashbar.show()
        }
    }
}
```

## Just import dependency from github
[![](https://jitpack.io/v/rkpatel097/FlashBar.svg)](https://jitpack.io/#rkpatel097/FlashBar)


# License

```
Copyright 2016 aritraroy

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

   http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.