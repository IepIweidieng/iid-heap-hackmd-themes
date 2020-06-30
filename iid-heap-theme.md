---
title: Style - IID 的文章堆 Iweidieng Iep's Article Heap
tags: theme
robots: noindex, nofollow
description: The Common Style of IID's Article Heap
---

<style>

/* Custom Style for Blog Pages by Iweidieng Iep */

:root {
  --article-width: 800px;
  --default-article-width: 760px;
  --article-title-height: 102px; /* Including margin and padding */
  --user-infobar-height: 92px; /* Including padding */
}

/* Prevent horizontal scrolling */
html[lang] > body[style] {
  overflow-x: hidden;
}

@keyframes slideUpIn {
  0% {
    transform: translatey(20px);
  }
  100% {
    transform: translatey(0);
  }
}
@keyframes slideDownIn {
  0% {
    transform: translatey(-20px);
  }
  100% {
    transform: translatey(0);
  }
}
@keyframes fadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: 1;
  }
}
@keyframes bgRepeat {
  0% {
    background-position: 0% 50%;
  }
  50% {
    background-position: 100% 50%;
  }
  100% {
    background-position: 0% 50%;
  }
}

/* Animated Fixed Background */
html[lang] > body[style]::before {
  position: fixed;
  content: "";
  height: 100%;
  width: 100%;
  z-index: -99999999;
  background: linear-gradient(270deg, #F1F8E9, #E3F2FD);
  background-size: 600% 600%;
  animation: bgRepeat 60s ease infinite;
}

/* Article Body */

#doc.markdown-body {
  margin: 0;
  padding-top: 0;
  padding-bottom: 80px;
  padding-left: 3px;
  padding-right: 3px;
  max-width: var(--article-width);
  width: unset;
  border: 17px solid white; /* Adjust the position of the paragraph comment button */
  background: white;
  box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
}
body[style] > #doc.markdown-body {
  padding-bottom: 60px;
}

#doc.markdown-body.comment-enabled.comment-inner {
  margin-right: 0;
}

/* Additional content after the ariticle */
.markdown-body ~ .container-fluid {
  margin-top: 40px;
}
@media screen and (min-width: 799px) {
  body[style] > #doc.markdown-body {
    margin-left: calc(50vw - var(--article-width) / 2);
  }
  .ui-view-area > #doc.markdown-body {
    margin-left: calc(50% - var(--article-width) / 2);
  }
}
@media screen and (min-width: 757px) {
  .markdown-body ~ .container-fluid {
    margin-left: calc(50vw - (var(--default-article-width) - 2px) / 2);
  }
  .ui-view-area > .container-fluid {
    margin-left: calc(50% - (var(--article-width) - 2px) / 2);
  }
}

/* Tool Windows */

/* Infobar Window */
.ui-infobar {
  position: absolute;
  top: var(--article-title-height);
  margin-top: 0;
  padding-top: 30px;
  padding-bottom: 20px;
  padding-left: 20px;
  padding-right: 20px;
  height: var(--user-infobar-height);
  max-width: var(--article-width);
  width: 100%;
}
@media screen and (min-width: 799px) {
  body[style] > .ui-infobar {
    margin-left: calc(50vw - var(--article-width) / 2);
  }
  .ui-view-area > .ui-infobar {
    margin-left: calc(50% - var(--article-width) / 2);
    left: 0;
  }
}
.ui-infobar > .row {
  margin-left: 0;
  margin-right: 0;
}
.ui-infobar__user-info > .list-inline {
  margin-bottom: 0;
  width: 100%;
}
/* Overlap the information of the last change user and the owner */
.ui-infobar__user-info > .list-inline > li, .ui-infobar > .pull-left > .list-inline > li {
  position: absolute;
  width: 100%;
}
.ui-infobar__user-info > ul > li:last-of-type, .ui-infobar > .pull-left > ul > li:last-of-type {
  margin-right: 0;
}
.ui-infobar .ui-lastchangeuser, .ui-infobar .ui-owner {
  display: block;
  width: 100%;
}
.ui-infobar .ui-lastchangeuser .ui-user-icon, .ui-infobar .ui-owner .ui-user-icon {
  height: 4.2em;
  width: 4.2em;
  border-radius: 100%;
  border: solid 1px white;
  box-shadow: 0 .25em .5em rgba(0, 0, 0, .175);
  transition: box-shadow .5s;
}
.ui-infobar .ui-lastchangeuser .ui-user-icon:hover:not(:active),
.ui-infobar .ui-owner .ui-user-icon:hover:not(:active) {
  box-shadow: 0 .25em .5em rgba(0, 0, 0, .35);
}
.ui-infobar .ui-lastchangeuser .ui-user-icon:active,
.ui-infobar .ui-owner .ui-user-icon:active {
  transition: box-shadow .2s;
}
.ui-infobar .ui-lastchangeuser::after, .ui-infobar .ui-owner::after {
  content: "@" attr(data-profile);
  background: white;
  display: inline-block;
  position: absolute;
  margin-left: .7em;
  font-size: 1.5em;
  line-height: 1em;
  width: calc(100% - 4.2em);
}
.ui-infobar .ui-status-lastchange, .ui-infobar .ui-no-lastchangeuser,
.ui-infobar .ui-owner span.text-uppercase {
  display: none;
}
.ui-infobar .ui-published-note {
  margin-left: 4.5em;
}
.ui-infobar .ui-lastchange {
  display: inline-block;
  position: absolute;
  margin-top: .4em;
  margin-left: 5em;
  top: 0;
  left: 0;
  line-height: 1.3em;
}
.ui-infobar .ui-lastchange::after {
  content: "\00000a\f073  " attr(data-createtime) "\00000a\f017  " attr(data-updatetime);
  font-family: medium-content-sans-serif-font, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif, FontAwesome;
  white-space: pre-wrap;
  display: inline-block;
  text-transform: none;
}
/* Actions */
.ui-infobar__actions, .ui-infobar > .pull-right {
  display: block;
  position: fixed;
  margin-bottom: 0;
  margin-right: 2.4px;
  padding: 5px 10px;
  bottom: 52px;
  left: calc(50% + var(--article-width) / 2);
  height: auto;
  white-space: nowrap;
  background: white;
  border: solid 1px rgba(176, 190, 197, .65);
  z-index: 101;
  transition: all .5s, left 1s ease-out;
}
.ui-view-area .ui-infobar > .pull-right {
  bottom: 20px;
  left: calc(50% + var(--article-width) / 2);
}
/* Compact mode */
@media screen and (max-width: 1279px) {
  .ui-infobar__actions, .ui-view-area .ui-infobar > .pull-right {
    padding: 5px 0;
    left: unset;
    right: 15px;
    opacity: .5;
    border-radius: 4px;
    background: transparent;
    border: none;
  }
  .ui-view-area .ui-infobar > .pull-right {
    left: unset;
    right: 15px;
  }
  .ui-infobar__actions:hover, .ui-view-area .ui-infobar__actions:focus-within,
  .ui-infobar > .pull-right:hover, .ui-view-area .ui-infobar > .pull-right:focus-within {
    opacity: 1;
  }
}
.ui-infobar__actions .list-inline, .ui-view-area .ui-infobar > .pull-right .list-inline {
  display: flex;
  flex-wrap: wrap;
  margin-top: auto;
  margin-bottom: auto;
  margin-left: 0;
}
.ui-infobar__actions .list-inline .btn,
.ui-infobar > .pull-right .list-inline .btn {
  transition: background .5s, color .5s;
}
.ui-infobar__actions .list-inline .btn:active,
.ui-infobar > .pull-right .list-inline .btn:active {
  transition: background .2s, color .2s;
}
.ui-infobar__actions > ul > li, .ui-infobar > .pull-right > ul > li {
  display: flex;
  flex-wrap: nowrap;
  margin-top: auto;
  margin-bottom: auto;
  width: max-content;
}
.ui-infobar__actions > ul > li:not(:last-of-type),
.ui-infobar > .pull-right > ul > li:not(:last-of-type) {
  padding-right: 5px;
}
.ui-infobar .ui-notification {
  margin-right: 0;
}
/* Make the dropdown menu drops up */
.ui-infobar .ui-notification .dropdown-menu {
  top: auto;
  bottom: 100%;
  margin-bottom: 2px;
  transition: all .5s;
}
@media screen and (max-width: 1082px) {
  .ui-infobar .ui-notification .dropdown-menu {
    font-size: 12px;
  }
}
.ui-infobar .ui-notification.open .dropdown-menu {
  animation: fadeIn .5s both ease-out, slideUpIn .5s both ease-out;
}
.ui-infobar .ui-notification.open .dropdown-menu .notification-menu-item {
  transition: background .5s, color .5s, opacity .5s;
}
.ui-infobar .ui-notification.open .dropdown-menu .notification-menu-item:active {
  transition: background .2s, color .2s, opacity .2s;
}
/* Fix deformed dropdown button when the dropdown menu is expanded */
.ui-infobar .ui-notification > button[data-toggle="dropdown"] {
  padding: 6.6px 5px;
  border-top-right-radius: 4px;
  border-bottom-right-radius: 4px;
  border-top-left-radius: 0;
  border-bottom-left-radius: 0;
}
.ui-view-area .ui-infobar .ui-notification > button[data-toggle="dropdown"] {
  padding: 5px 5px;
}
.ui-infobar .ui-notification > button[data-toggle="dropdown"]::after {
  content: "\f0d8"; /* A triangle arrow pointing up (FontAwesome) */
  font-family: FontAwesome;
}

/* TOC Window */
#ui-toc-affix {
  background: white;
  border: solid 1px rgba(176, 190, 197, .65);
  transition: width .5s, max-width .5s, left .5s ease-out;
}
@media screen and (min-width: 1083px) {
  body[style] > #ui-toc-affix {
    display: block !important;
  }
}
#ui-toc-affix a, .ui-toc #ui-toc a {
  display: block;
  transition: all .5s;
}
.ui-toc #tocLabel {
  transition: background .5s, color .5s, opacity .5s;
}
.ui-toc #tocLabel:active {
  transition: background .2s, color .2s, opacity .2s;
}
.ui-toc #tocLabel[aria-expanded="true"] ~ #ui-toc {
  animation: fadeIn .5s both ease-out, slideUpIn .5s both ease-out;
}

/* Comment Window */
.ui-comment-app .open-comments {
  /*position: fixed;
  top: 71px;
  margin: 20px 0;*/
  background: transparent;
}
.ui-comment-app .open-comments #comment-settings {
  animation: fadeIn .5s both ease-out;
}
.ui-comment-app .open-comments .popover {
  animation: fadeIn .5s both ease-out;
}
.ui-comment-app .comments-scroller .comments-containers > div {
  animation: fadeIn .5s both ease-out, slideUpIn .5s both ease-out;
}

/* Footer */
footer {
  background-color: #f2f3f5;
  border: none;
  border-top: solid 1px rgba(176, 190, 197, .15);
  height: 48px;
  align-items: center;
}
footer .footer {
  padding: calc((27.2px - 21.433px) / 2) 0;
}
  
/* Custom Markdown Style */

.markdown-body > style + h1:first-of-type {
  margin-left: 0;
  margin-right: 0;
}
.markdown-body > style + h1:first-of-type + * {
  margin-top: var(--user-infobar-height);
}
.markdown-body h1 {
  border-image: radial-gradient(circle at 50%, #eceff1 50%, #fafafa) 0 0 1 0 / 0 0 1px 0;
}
.markdown-body h2 {
  border-image: radial-gradient(circle at 25%, #eceff1 50%, #fafafa) 0 0 1 0 / 0 0 1px 0;
}

/* Language tag for code blocks */
.markdown-body pre {
  position: relative;
}
.markdown-body pre > code.hljs::before {
  position: absolute;
  display: inline-block;
  content: attr(class); /* Contains redundant words to remove */
  text-align: right;
  width: min-content;
  white-space: break-spaces; /* Force wrapping on spaces */
  line-height: 1.1em;
  clip-path: inset(0 0 1em 0); /* Hide non-first lines */
  opacity: 0.5;
  top: .3em;
  right: 0.5em;
  font-family: Roboto;
  font-size: .9em;
  font-weight: 900;
  letter-spacing: normal;
}

/* Make the checkbox appear to be enabled */
.markdown-body input:disabled[type="checkbox"] {
    color: unset;
}

/* Inline spoiler */
.markdown-body em > pre:only-child, .markdown-body em > code:only-child,
.markdown-body em > strong:only-child > pre:only-child, .markdown-body em > strong:only-child > code:only-child {
  position: relative;
  font: unset;
  font-style: normal;
  white-space: pre;
  padding-top: .2em;
  padding-bottom: .2em;
  border-radius: 3px;
  transition: color .5s, background .5s;
}
.markdown-body em > pre:only-child:active, .markdown-body em > code:only-child:active,
.markdown-body em > strong:only-child > pre:only-child:active, .markdown-body em > strong:only-child > code:only-child:active {
  color: rgba(0, 0, 0, .7) !important;
  background: rgba(160, 160, 160, .4);
  transition: none;
}

@keyframes inlineSpoilerExpand {
  0% {
    cursor: pointer;
    z-index: 0;
  }
  100% {
    opacity: 0;
    cursor: auto;
    z-index: -1;
  }
}
@keyframes inlineSpoilerCollapse {
  0%, 100% {
    background: #a0a0a0;
  }
  20% {
    background: #b0b0b0;
  }
}
.markdown-body em > pre:only-child::after, .markdown-body em > code:only-child::before,
.markdown-body em > strong:only-child > pre:only-child::after, .markdown-body em > strong:only-child > code:only-child::before {
  content: none;
}
.markdown-body em > pre:only-child::after, .markdown-body em > code:only-child::after,
.markdown-body em > strong:only-child > pre:only-child::after, .markdown-body em > strong:only-child > code:only-child::after {
  position: absolute;
  display: block;
  content: "";
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  opacity: 1;
  background: #a0a0a0;
  border-radius: 3px;
  animation: inlineSpoilerExpand .016s forwards paused;
  transition: opacity .5s, background .5s;
}
.markdown-body em > pre:only-child:hover::after, .markdown-body em > code:only-child:hover::after,
.markdown-body em > strong:only-child > pre:only-child:hover::after, .markdown-body em > strong:only-child > code:only-child:hover::after {
  background: #c0c0c0;
}
.markdown-body em > pre:only-child:active::after, .markdown-body em > code:only-child:active::after,
.markdown-body em > strong:only-child > pre:only-child:active::after, .markdown-body em > strong:only-child > code:only-child:active::after {
  opacity: 1;
  animation-play-state: running;
  transition: all .2s;
}
.markdown-body :not(:hover) > em > pre:only-child::after, .markdown-body :not(:hover) em > code:only-child::after,
.markdown-body :not(:hover) > em > strong:only-child > pre:only-child::after, .markdown-body :not(:hover) > em > strong:only-child > code:only-child::after {
  animation: inlineSpoilerCollapse .5s forwards;
}

/* Collapsible spoiler */
.markdown-body details[open] > *:not(summary) {
  animation: fadeIn .5s both ease-out, slideDownIn .5s both ease-out;
}

/* Links */
.markdown-body a {
  background-color: transparent;
  transition: background-color .5s;
}
.markdown-body a:hover {
  background-color: #00bcd420;
}
.markdown-body a:active {
  transition: background-color .2s;
}

/* User tags */
.markdown-body a[href^="/@"][style*="--data-image"]::before {
  content: "";
  background-image: var(--data-image);
  background-size: contain;
  display: inline-block;
  height: 1.2em;
  width: 1.2em;
  line-height: 1.2em;
  border-radius: 100%;
  border: solid 1px white;
  box-shadow: 0 .25em .5em rgba(0, 0, 0, .175);
  transition: box-shadow .5s;
}
.markdown-body a[href^="/@"][style*="--data-image"]:hover:not(:active)::before {
  box-shadow: 0 .25em .5em rgba(0, 0, 0, .35);
}
.markdown-body a[href^="/@"][style*="--data-image"]:active::before {
  transition: box-shadow .2s;
}
.markdown-body a[href^="/@"][style*="--data-image"]::after {
  content: attr(href);
  display: inline;
  position: relative;
  margin-left: calc(.2em + -.8ch);
  color: #888;
  font-size: .8em;
  font-weight: 400;
  clip-path: inset(0px 0px 0px .8ch);
}

/* Invisible text */
.markdown-body .stealth {
  position: absolute;
  font-size: 0;
  color: transparent;
}

/* Article List */
/* Usage:
:::info article
:::
*/

.markdown-body .alert-info.article {
  color: black;
  background-color: transparent;
  border: none;
  transition: all .5s;
}
.markdown-body .alert-info.article:hover {
  box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
}

/* Article Title Links */
.markdown-body .alert-info.article > h2 {
  position: relative;
  border-bottom: solid 1px #e7e7e7; /* Make space for the border */
}
.markdown-body .alert-info.article > h2 .anchor + a {
  display: block;
  text-decoration: none;
  color: #37474f;
  transition: all .5s;
}
.markdown-body .alert-info.article > h2 .anchor + a:hover:not(:active) {
  color: #546e7a;
  background-color: transparent;
}
.markdown-body .alert-info.article > h2:active .anchor + a {
  transition: all .2s;
}
.markdown-body .alert-info.article > h2 .anchor + ::after {
  display: block;
  content: "";
  position: absolute;
  height: 4px;
  width: 0;
  left: 2em;
  bottom: 0;
  background: #2196F3;
  transition: all .5s;
}
.markdown-body .alert-info.article > h2:hover:not(:active) ::after {
  left: 0;
  width: 100%;
}
.markdown-body .alert-info.article > h2:hover:active ::after {
  transition: all .2s;
}

/* Timestamp */
.markdown-body .alert-info.article > h2:first-child {
  margin-top: 10px;
}
.markdown-body .alert-info.article > h2:first-of-type {
  margin-bottom: 0;
}
.markdown-body .alert-info.article > h2:first-of-type + blockquote {
  border-left: none;
  padding-top: .2em;
  padding-left: 1em;
  line-height: 2em;
  font-size: .9em;
}

/* Read-More Links */
.markdown-body .alert-info.article p:last-of-type > a:only-child {
  position: relative;
}
.markdown-body .alert-info.article p:last-of-type > a:only-child::after {
  position: absolute;
  bottom: .2em;
  right: .5em;
  content: "\f101";
  font: normal normal normal .8em/1 FontAwesome;
  opacity: 0;
  transition: right .5s, opacity .5s;
  pointer-events: none;
}
.markdown-body .alert-info.article p:last-of-type > a:only-child:hover:not(:active)::after {
  right: -.8em;
  opacity: 1;
}
.markdown-body .alert-info.article p:last-of-type > a:only-child:active::after {
  transition: right .2s, opacity .2s;
}

/* Category & Tags */
.markdown-body .alert-info.article > h6[id^="tags"] {
  margin-top: 34px;
  margin-bottom: 10px;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code {
  position: relative;
  padding-left: calc(.8em + .5em);
  padding-right: 1em;
  margin-right: .2em;
  background: transparent;
  line-height: 2.4em;
  white-space: nowrap;
  text-transform: capitalize;
  font-size: 12px;
  z-index: 0;
  cursor: pointer;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code:hover:not(:active) {
  color: rgba(0, 0, 0, 0.77) !important;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code:active {
  transition: all .2s;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code::before {
  position: absolute;
  content: "";
  display: inline-block;
  top: 0;
  left: 0;
  height: 100%;
  width: 100%;
  z-index: -1;
  background: linear-gradient(to right, #b3e5fc 45%, #e1f5fe 55%);
  background-size: 400% 400%;
  background-position: 75% 100%;
  padding-left: 0;
  padding-right: 0;
  clip-path: polygon(.8em 0%, 100% 0%, 100% 100%, .8em 100%, 0 50%);
  transition: all .5s;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code:first-of-type::before {
  background: linear-gradient(to right, #ffe0b2 45%, #fff3e0 55%);
  background-size: 400% 400%;
  background-position: 75% 100%;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code:hover:not(:active)::before {
  background-position: 0% 25%;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code:active::before {
  transition: all .2s;
}
.markdown-body .alert-info.article > h6[id^="tags"] > code::after {
  position: absolute;
  display: inline-block;
  margin: auto 0;
  top: 0;
  bottom: 0;
  left: 0;
  right: calc(100% - (.8em + 1em - .55em));
  content: "";
  color: black;
  background: white;
  clip-path: circle(.2em);
}

.markdown-body::after {
  position: relative;
  display: block;
  content: "© 2020 Iweidieng Iep";
  top: 15px;
  left: 25px;
  color: #9e9e9e;
  font-size: 14px;
}

</style>