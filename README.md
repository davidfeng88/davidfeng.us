# Personal Website

Built using Hugo.

Location: https://davidfeng.us/

## Getting Started

0. Install git, VSCode, hugo.
1. `git clone --recurse-submodules https://github.com/davidfeng88/davidfeng.us.git`
2. `code davidfeng.us`
3. `hugo server` then go to http://localhost:1313/.
4. `hugo new posts/a/index.md` to create a new post. use `index.zh-cn.md` for Chinese posts.

See https://logseq-public.pages.dev/#/page/hugo for more.

## Create a new post

1. `hugo new posts/date-title/index.zh-cn.md`
2. For images
  1. Compress them to jpeg with 200-300kB size (on windows use Riot).
  2. Prefer the `figure` shortcode over markdown syntax (`![](./foo.jpg)`). (`figure` can have title and also auto centers)
  3. Add `images: ['foo.jpg']` in front matter for Twitter Cards.
3. Add tags, e.g. `admin`, `travel`, `trip`, `reading`.
  1. If the blog is a travel log, add `travel/游记`, country/state/city.
  2. Consider add the theme, like `math/history/career/职业发展/chemistry`.
  3. Add `meta` for admin posts.
  4. Add `tech/frontend` etc. for technical posts.
  5. Add `book-review/读书笔记` for book reviews.
4. Preview by `hugo server` and revise.
5. Translate to English with Claude. Add `(Translated from the Chinese version with the help of Claude.)` and proofread.
  - for reasons unknown to me, if the post contains images, they won't show up properly in the Chinese version if the English version does not exist.
