---
title: IID 的文章堆 ~ Iweidieng Iep's Article Heap
tags: blog
robots: noindex, nofollow
description: The Book Theme of IID's Article Heap
---

<style>

/* Custom Style for Book Mode by Iweidieng Iep */

:root {
  --topbar-height: 45px;
  --topbar-button-width: 42px;
  --sidebar-width: 360px;
  --contact-bar-height: 50px;
  --article-width: 800px;
  --default-article-width: 760px;
  --sidebar-always-float-width: 1520px;
}

/* Allow pull-to-refresh and prevent elements from being placed under the scroll bar */
html[lang] {
  overflow: auto;
  overflow: initial;
}
html[lang] > body[style] {
  overflow: auto;
  overflow: initial;
  overflow-x: hidden;
  font-family: medium-content-sans-serif-font, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}

@keyframes titleHoverRepeat {
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
@keyframes slideDownIn {
  0% {
    transform: translatey(-20px);
  }
  100% {
    transform: translatey(0);
  }
}
@keyframes slideLeftIn {
  0% {
    transform: translatex(-20px);
  }
  100% {
    transform: translatex(0);
  }
}
@keyframes slideRightIn {
  0% {
    transform: translatex(20px);
  }
  100% {
    transform: translatex(0);
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
@keyframes upperHalfFadeIn {
  0% {
    opacity: 0;
  }
  100% {
    opacity: .3;
  }
}
@keyframes lowerHalfFadeIn {
  0% {
    opacity: .3;
  }
  100% {
    opacity: 1;
  }
}
.topbar {
  position: relative;
  top: 0;
  height: var(--topbar-height);
  width: 100%;
  background: white;
  border-bottom: solid 1px #B0BEC5;
  box-shadow: none;
  animation: fadeIn 1s both ease-out;
}
.book-container, .book-container.open {
  position: relative;
  margin-left: auto;
  margin-right: 0;
  padding-top: 0;
  top: auto;
  bottom: 0;
  left: auto;
  right: 0;
  max-height: calc(100% - var(--topbar-height)) !important;
  width: 100%;
  overflow: hidden;
  box-shadow: none;
  overscroll-behavior: auto;
  transition: all 1s;
}

/* Fix oversized window which makes the footer disappear on phones */
.book-container iframe, .book-container.open iframe {
  max-height: calc(100% - var(--topbar-height)) !important;
  animation: upperHalfFadeIn 1s both linear, lowerHalfFadeIn 1s forwards ease-out paused, slideDownIn 1s both ease-out paused;
}
.book-container iframe[loaded="true"] {
  animation-play-state: running;
}

/* Fade out the book container when using the side bar on small screen */
.container-mask {
  z-index: 2;
  display: block;
  left: 100%;
  margin-left: 0;
  background: #ffffffa0;
  opacity: 0;
  width: 100%;
  transition: opacity 1s, left 0s linear 1s;
}
.summary.open ~ .container-mask {
  left: 0;
  opacity: 1;
  transition: opacity 1s, left 0s linear;
}

/* The space is enough to allow browsing while side bar is open */
@media screen and (min-width: 799px) {
  .summary.open ~ .container-mask {
    left: 100%;
    opacity: 0;
    transition: opacity 1s, left 0s linear 1s;
  }
  .book-container {
    top: auto;
    bottom: 0;
    left: auto;
    right: 0;
  }
  .book-container.open {
    width: calc(100% - var(--sidebar-width));
    filter: none;
  }
  .book-container.open iframe {
    width: calc(100% - var(--sidebar-width));
  }
}
@media screen and (min-width: 1520px) {
  .book-container.open, .book-container.open iframe {
    width: 100%; /* The space is enough to avoid overlapping */
  }
}

/* Side Bar Opening Button and other Action Buttons */

/* The search box */
.summary .toolbar .search {
  flex: 1;
  margin: auto;
  min-width: 100px;
  font-family: "Source Sans Pro", Helvetica, Arial, "PingFang TC", "Microsoft JhengHei", "微軟正黑", sans-serif;
}
/* Fade out the page body when using the search box */
.summary .toolbar .search::before {
  display: block;
  position: absolute;
  content: "";
  top: 0;
  left: 0;
  width: calc(100vw + var(--sidebar-width));
  height: 100%;
  z-index: 0;
  background: #ffffffa0;
  /* Leave space for the search box */
  clip-path: polygon(0 var(--topbar-height), var(--sidebar-width) var(--topbar-height), var(--sidebar-width) 0, calc(100vw + var(--sidebar-width)) 0, calc(100vw + var(--sidebar-width)) 100%, 0 100%);
  opacity: 0;
  pointer-events: none;
  transition: opacity 1s;
}
.summary.open .toolbar .search:focus-within::before {
  opacity: 1;
}
.toolbar .ui-summary-search {
  display: inline;
  margin: auto 5px;
  width: calc(100% - 5px * 2);
}
/* Other action buttons */
.summary .toolbar .ui-summary-action, .topbar .ui-summary-action {
  position: relative;
  display: flex;
  align-items: stretch;
  flex: 0;
  border: none;
  padding: 0;
  opacity: 1;
  background-color: transparent;
  color: #555555;
  font-weight: 900;
  transition: all .5s;
}
.topbar .ui-summary-action {
  animation: fadeIn 1s both ease-out .5s;
}
.summary .toolbar .ui-summary-action {
  min-width: var(--topbar-button-width);
}
.summary .toolbar .ui-summary-action > .fa, .topbar .ui-summary-action > .fa {
  display: inline;
  margin: auto;
  font-size: 1.2em;
}
/* The summary opening button */
.topbar > .ui-summary-open {
  animation: none;
}
.topbar .ui-summary-open > span.visible-xs-inline {
  display: none !important; /* Hide the text */
}
.topbar .ui-summary-open > .fa-angle-double-right::before {
  content: "\f0c9"; /* Replace the icon with the icon of `.fa-bars` */
}
.summary.open ~ .topbar > .ui-summary-open {
  opacity: 0;
  pointer-events: none;
}
.summary .toolbar .ui-summary-action:hover, .topbar .ui-summary-action:hover {
  background-color: #00bcd460;
}
.summary .toolbar .ui-summary-action:active, .topbar .ui-summary-action:active {
  background-color: #00bcd4;
  color: #ffffff;
  transition: all .2s;
}
.topbar .ui-summary-action .fa {
  padding-left: 15px;
  padding-right: 15px;
}
@media screen and (min-width: 799px) {
  .summary ~ .topbar > .ui-summary-open {
    margin-left: calc(50% - var(--article-width) / 2);
  }
  .summary:hover ~ .topbar > .ui-summary-open {
    opacity: 0;
    pointer-events: none;
  }
  .summary:hover .toolbar .search:focus-within::before {
    opacity: 1;
  }
}

/* Side Bar */

.summary .toolbar, .topbar {
  display: flex;
  align-items: stretch;
  justify-content: flex-start;
  flex-flow: row wrap;
  left: 0;
  padding-left: 0;
  padding-top: 0;
}
.summary .toolbar {
  justify-content: flex-end;
  top: 0;
  height: var(--topbar-height);
  z-index: 4;
  background: #f2f3f5;
  position: static;
  text-align: right;
  line-height: var(--topbar-height);
  box-shadow: none;
  border: none;
}
@media screen and (min-width: 799px) {
  .summary .toolbar {
    z-index: 4;
    background: #f2f3f5;
    top: 0;
    height: var(--topbar-height);
  }
  .summary:hover ~ .topbar > .ui-summary-open {
    opacity: 0;
    pointer-events: none;
  }
}

.summary {
  position: absolute;
  top: 0;
  padding: 0;
  border: none;
  box-shadow: none;
  background: transparent;
  transition: all .5s;
  overscroll-behavior: contain;
}
.summary, #summary > ul:last-of-type {
  left: calc(0px - var(--sidebar-width));
  width: var(--sidebar-width);
  max-width: 100%;
}
.summary.open {
  box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
}
.summary.open, .summary.open #summary > ul:last-of-type {
  left: 0;
}
.summary::after {
  position: absolute;
  display: block;
  content: "© 2020 Iweidieng Iep";
  bottom: calc(46.8px + 5px);
  right: 25px;
  z-index: 4;
  color: #9e9e9e;
  pointer-events: none;
  transition: text-shadow;
}
.summary.open::after {
  text-shadow: 0 6px 12px rgba(255, 255, 255, .175);
}
.summary #summary {
  position: relative;
  height: calc(100% - var(--topbar-height) - 46.8px);
  overflow: auto;
}
html[lang] .summary #summary {
  font-family: medium-content-sans-serif-font, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}
.summary h1, .summary h2, .summary h3, .summary h4, .summary h5, .summary h6 {
  font-weight: 580;
}
.summary #summary {
  background: linear-gradient(to right, #FFFFFF00 1%, #FFFFFFFF 99%);
}
#summary > ul:first-of-type ~ * {
  animation: fadeIn .5s both ease-out, slideDownIn .5s both ease-out;
}
#summary > ul:last-of-type {
  background: linear-gradient(to right, #F3F3F300 1%, #F3F3F3FF 99%);
  animation: none;
}
#summary > ul:last-of-type > li {
  animation: fadeIn .5s both ease-out .5s, slideLeftIn .5s both ease-out .5s;
}
.summary #summary {
  background-size: 200% 100%;
  background-position: 0% 80%;
  transition: all .5s;
}
#summary > ul:last-of-type {
  background: linear-gradient(to right, #F3F3F300 1%, #F3F3F3FF 99%);
  background-size: 200% 100%;
  background-position: 0% 80%;
  transition: all .5s;
}
.summary.open #summary, .summary.open #summary > ul:last-of-type {
  background-size: 10000% 100%;
  background-position: 99% 100%;
}
.summary:not(.open) #summary:not(:hover) {
  overflow: hidden;
}
@media screen and (min-width: 799px) {
  .summary, #summary > ul:last-of-type {
    padding-top: 0;
    padding-left: 0;
    left: calc(0px - var(--sidebar-width) + 5px); /* Leave space for hovering-to-open action */
    box-shadow: none;
  }
  .summary:hover {
    box-shadow: 0 6px 12px rgba(0, 0, 0, .175);
  }
  .summary:hover::after {
    text-shadow: 0 6px 12px rgba(255, 255, 255, .175);
  }
  .summary:hover, .summary:hover #summary > ul:last-of-type {
    left: 0;
  }
  .summary #summary, .summary.open:not(:hover) #summary,
  .summary #summary > ul:last-of-type, .summary.open:not(:hover) #summary > ul:last-of-type {
    background-size: 10000% 100%;
    background-position: 30% 31%;
  }
  .summary.open:not(:hover)::after {
    text-shadow: none;
  }
  .summary:hover #summary, .summary:hover #summary > ul:last-of-type {
    background-size: 10000% 100%;
    background-position: 99% 100%;
  }
}

/* Side Bar Items */

/* Title */
#summary > ul:first-of-type ~ h1 {
  position: relative;
  padding: 0;
}
#summary > ul:first-of-type ~ h1 * {
  display: block;
  margin: 0;
  padding: 15px;
  width: 100%;
}

/* Section Title */
#summary > ul:first-of-type ~ .collapsible {
  z-index: 3;
}
#summary > ul:first-of-type ~ .collapsible + :not(.collapsible) {
  position: relative;
  top: -10%;
  max-height: 0%;
  opacity: 0;
  z-index: 2;
  transition: opacity .5s, top .5s;
  animation: none;
}
/* Fix `.collapsed` causing `.collapsible` to be expanded instead of being collapsed */
/* Expanded by default */
#summary > ul:first-of-type ~ .collapsible:not(.collapsed) + :not(.collapsible) {
  top: 0;
  max-height: none;
  opacity: 1;
}
#summary > ul:first-of-type ~ .collapsible .collapsible-icons .fa-angle-down::before {
  content: "\f106"; /* `fa-angle-up */
}
#summary > ul:first-of-type ~ .collapsible.collapsed .collapsible-icons .fa-angle-down {
  transform: rotate(180deg) translate(1px, 0);
}
#summary > ul:first-of-type ~ :not(ul)[data-startline] {
  border-top: solid 1px #e7e7e7; /* Make space for the border */
  border-image: radial-gradient(circle at 25%, #eceff1 50%, #fafafa) 1 0 0 0 / 1px 0 0 0; /* The actual border */
}
#summary > ul:first-of-type ~ .collapsible .collapsible-icons {
  position: absolute;
  left: calc(var(--sidebar-width) - 32px);
}

/* Hover and Active Effects */

/* Background fading effect */
#summary > ul:first-of-type ~ [data-startline],
#summary > ul:first-of-type ~ .collapsible + :not(.collapsible)[data-startline],
#summary > ul:first-of-type ~ * [data-startline],
#summary > ul:first-of-type ~ * .collapsible + :not(.collapsible)[data-startline] {
  background-color: transparent;
  transition:  background-color .5s ease-out, opacity .5s, top .5s, left .5s, background-size .5s, background-position .5s;
}
#summary > ul:first-of-type ~ [data-startline]:hover:not(:active),
#summary > ul:first-of-type ~ .collapsible:hover:not(:active) + :not(.collapsible)[data-startline],
#summary > ul:first-of-type ~ * [data-startline]:hover:not(:active),
#summary > ul:first-of-type ~ * .collapsible:hover:not(:active) + :not(.collapsible)[data-startline] {
  background-color: #00bcd420;
}
#summary > ul:first-of-type ~ [data-startline]:active,
#summary > ul:first-of-type ~ .collapsible:active + :not(.collapsible)[data-startline],
#summary > ul:first-of-type ~ * [data-startline]:active,
#summary > ul:first-of-type ~ * .collapsible:active + :not(.collapsible)[data-startline] {
  transition: background-color .2s ease-out, opacity .5s, top .5s, left .5s, background-size .5s, background-position .5s;
}

/* Sliding effect and padding */
#summary > ul:first-of-type ~ :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ .collapsible + :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ * :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ * .collapsible + :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ .collapsible > .heading-span,
#summary > ul:first-of-type ~ * .collapsible > .heading-span {
  border-left: 6px solid transparent;
  border-right: 6px solid transparent;
  transition: all .5s ease-out;
}
#summary > ul:first-of-type ~ :not(.collapsible):not(ul)[data-startline]:hover:not(:active),
#summary > ul:first-of-type ~ .collapsible:hover:not(:active) + :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ * :not(.collapsible):not(ul)[data-startline]:hover:not(:active),
#summary > ul:first-of-type ~ * .collapsible:hover:not(:active) + :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ .collapsible:hover:not(:active) > .heading-span,
#summary > ul:first-of-type ~ * .collapsible:hover:not(:active) > .heading-span {
  border-left-width: 12px;
  border-right-width: 0px;
}
#summary > ul:first-of-type ~ :not(.collapsible):not(ul)[data-startline]:active,
#summary > ul:first-of-type ~ .collapsible:active + :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ * :not(.collapsible):not(ul)[data-startline]:active,
#summary > ul:first-of-type ~ * .collapsible:active + :not(.collapsible):not(ul)[data-startline],
#summary > ul:first-of-type ~ .collapsible:active > .heading-span,
#summary > ul:first-of-type ~ * .collapsible:active > .heading-span {
  transition: all .2s ease-out;
}

/* Special color for active links */
#summary > ul:first-of-type ~ * [data-startline].active,
#summary > ul:first-of-type ~ * .collapsible.active + :not(.collapsible)[data-startline] {
  background-color: #00bcd4;
}
#summary > ul:first-of-type ~ * [data-startline].active:hover:not(:active),
#summary > ul:first-of-type ~ * .collapsible.active:hover:not(active) + :not(.collapsible)[data-startline] {
  background-color: #00bcd4c0;
}
#summary > ul:first-of-type ~ * [data-startline].active > a,
#summary > ul:first-of-type ~ * .collapsible.active + :not(.collapsible)[data-startline] > a {
  color: #ffffff;
}

/* Label shorthand */
#summary > ul:first-of-type ~ * * > a > em strong {
  display: inline;
  padding: .2em .6em .3em;
  font-size: 75%;
  font-weight: 700;
  font-style: normal;
  line-height: 1;
  color: #fff;
  text-align: center;
  white-space: nowrap;
  vertical-align: baseline;
  border-radius: .25em;
}
#summary > ul:first-of-type ~ * *:focus-within > a > em strong,
#summary > ul:first-of-type ~ * *:hover > a > em strong {
  color: #fff;
}
#summary > ul:first-of-type ~ * * > a > em > strong { background-color: #777; }
#summary > ul:first-of-type ~ * *:focus-within > a > em strong,
#summary > ul:first-of-type ~ * *:hover > a > em strong { background-color: #5e5e5e; }

/* Top Bar */

/* Title */
#summary > .collapsible:first-child {
  position: fixed;
  list-style-type: none;
  display: inline-block;
  z-index: -1;
  margin: 0;
  padding: 0 25px;
  top: 0;
  left: 50%;
  height: var(--topbar-height);
  max-height: none;
  max-width: none;
  transform: translate(-50%, 0);
  cursor: auto;
  font-family: Roboto;
  font-size: 24px;
  letter-spacing: 4px;
  background: transparent;
  color: #555555;
  text-shadow: none;
  overflow: visible;
  transition: all .5s;
}
#summary > .collapsible:first-child > .heading-span {
  z-index: -1;
  display: inline-block;
  padding: 0;
  line-height: var(--topbar-height);
  max-width: none;
  white-space: nowrap;
  overflow: visible;
  transition: all .5s;
  animation: fadeIn 1s both ease-out 1s, slideLeftIn 1s both ease-out 1s;
}
#summary > .collapsible:first-child:hover > .heading-span {
  color: #6a6a6a;
  -webkit-text-fill-color: transparent;
  background: linear-gradient(270deg, #1B5E20, #01579B, #4A148C);
  -webkit-background-clip: text;
  background-size: 600% 600%;
  animation: fadeIn 1s both ease-out 1s, slideLeftIn 1s both ease-out 1s, titleHoverRepeat 20s ease infinite .5s;
  text-shadow: 0 6px 24px #01579B80, 0 6px 12px #ffffff80;
}
#summary > .collapsible:first-child .fa {
  display: none;
  padding: 0;
  max-height: 0;
}
@media screen and (min-width: 1159px) and (max-width: 1519px) {
  .summary.open > #summary > .collapsible:first-child {
    left: calc(var(--sidebar-width) + (100% - var(--sidebar-width)) / 2);
    transform: translate(-50%, 0);
  }
}
@media screen and (min-width: 799px) and (max-width: 1158px) {
  .summary.open > #summary > .collapsible:first-child {
    left: var(--sidebar-width);
    transform: translate(0, 0);
  }
}
@media screen and (max-width: 798px) {
  #summary > .collapsible:first-child .heading-span {
    letter-spacing: 0.5vw;
  }
}
@media screen and (max-width: 498px) {
  #summary > .collapsible:first-child .heading-span {
    font-size: calc(.1em + 4vw);
  }
}

/* Navigation Bar */
#summary > ul:first-of-type {
  position: relative;
  display: flex;
  flex-flow: column nowrap;
  justify-content: flex-start;
  align-items: stretch;
  padding: 0;
  top: 0;
  left: 0;
  height: auto;
  width: 100%;
  max-height: none;
  overflow-x: auto;
  font-weight: 600;
  transition: all 1s;
}
@media screen and (min-width: 799px) {
  #summary > ul:first-of-type {
    position: fixed;
    flex-flow: row nowrap;
    justify-content: flex-end;
    align-items: stretch;
    margin-left: auto;
    margin-right: calc(50% - var(--article-width) / 2);
    left: unset;
    right: 0;
    height: var(--topbar-height);
    max-width: var(--article-width);
    width: auto;
    z-index: -1;
  }
  .summary.open > #summary > ul:first-of-type {
    margin-right: 0;
  }
}
@media screen and (min-width: 1159px) and (max-width: 1519px) {
  .summary.open > #summary > ul:first-of-type {
    margin-right: calc((100% - var(--sidebar-width) - var(--article-width)) / 2);
  }
}
@media screen and (min-width: 1520px) {
  .summary.open > #summary > ul:first-of-type {
    margin-right: calc((100% - var(--article-width)) / 2);
  }
}

/* Navigation Items */
#summary > ul:first-of-type > li {
  position: relative;
  max-height: none;
  display: flex;
  justify-content: center;
  list-style-type: none;
  flex: 1 1 0;
  margin: auto;
  width: 100%;
  background-color: transparent;
  transition: all .5s ease-out;
  animation: fadeIn 1s both ease-out .5s;
}
#summary > ul:first-of-type > li:hover:not(:active) {
  background-color: #00bcd460;
}
#summary > ul:first-of-type > li:active {
  transition: all .2s ease-out;
}
#summary > ul:first-of-type > li.active {
  background-color: #00bcd4;
}
#summary > ul:first-of-type > li.active:hover:not(:active) {
  background-color: #00bcd4c0;
}
#summary > ul:first-of-type > li > a {
  position: static;
  margin: auto;
  border: none;
  padding-left: 25px;
  padding-right: 15px;
  height: auto;
  width: 100%;
}
#summary > ul:first-of-type > li.active > a {
  color: #ffffff;
}
@media screen and (min-width: 799px) {
  #summary > ul:first-of-type > li {
    width: auto;
    height: var(--topbar-height);
  }
  #summary > ul:first-of-type > li > a {
    padding-left: 15px;
    width: auto;
  }
}

/* Contact Links */

#summary > h6:last-of-type {
  display: none;
  padding: 0;
  max-height: 0;
}
#summary > h6:last-of-type .fa {
  display: none;
  padding: 0;
  max-height: 0;
}
#summary > ul:last-of-type {
  position: fixed;
  display: flex;
  flex-flow: row nowrap;
  justify-content: space-evenly;
  padding: 0;
  bottom: 0;
  height: var(--contact-bar-height);
  max-height: none;
  border-left: none;
}
#summary > ul:last-of-type:hover:not(:active) {
  border-left-width: 0;
  background-color: transparent;
}
#summary > ul:last-of-type > li:not(.collapsible)[data-startline] {
  flex: 1 1 0;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  text-align: center;
  border-left: none;
  margin: 0;
  padding: auto;
  border-left: none;
  border-right: none;
  height: auto;
}
#summary > ul:last-of-type:hover:not(:active) > li,
#summary > ul:last-of-type:active > li,
#summary > ul:last-of-type > li:not(.collapsible)[data-startline]:active {
  border-left-width: 0px;
  border-right-width: 0px;
}
#summary > ul:last-of-type > li:not(.collapsible)[data-startline]:hover:not(:active) {
  border-left-width: 0px;
  border-right-width: 0px;
  background-color: #00bcd460;
}
#summary > ul:last-of-type > li:active {
  background-color: #00bcd4;
  color: #ffffff;
  transition: all .2s;
}
#summary > ul:last-of-type > li > a {
  position: static;
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  padding: 5px;
  margin: auto;
  height: auto;
  width: 100%;
  font-size: 10px;
}
#summary > ul:last-of-type > li > a > i {
  display: flex;
  flex-flow: column nowrap;
  justify-content: center;
  margin: 0;
  font-size: 18px;
  line-height: 1.2em;
}
#summary > ul:last-of-type > li:active > a {
  color: #ffffff;
  transition: all .2s;
}
#summary > ul:last-of-type .fa-external-link {
  display: none;
}

/* Links and Buttons */

#summary a {
  text-decoration: none;
}
#summary > h1:first-of-type ~ * a::after,
.summary .ui-summary-action::after,
.topbar .ui-summary-action::after {
  display: block;
  content: "";
  position: absolute;
  height: 4px;
  width: 0;
  bottom: 0;
  left: 0;
  background: #2196F3;
  transition: all .5s;
}
#summary > ul:first-of-type ~ * a::after {
  left: 2em;
}
#summary > ul:last-of-type > li > a::after {
  left: 0;
}
#summary > h1:first-of-type ~ * a:hover:not(:active)::after,
.summary .ui-summary-action:hover:not(:active)::after,
.topbar .ui-summary-action:hover:not(:active)::after {
  width: 100%;
  left: 0;
}
#summary > ul:first-of-type ~ * a:hover:not(:active)::after {
  width: calc(100% - 12px);
}
#summary > ul:last-of-type > li > a:hover:not(:active)::after {
  width: 100%;
  left: 0;
}
#summary > h1:first-of-type ~ * a:active::after,
.summary .ui-summary-action:active::after,
.topbar .ui-summary-action:active::after {
  transition: all .2s;
}

</style>

# IID's Article Heap
- [Home](/@IID/IID-Heap-Home)
- [About](/@IID/IID-Heap-About)

# [IID 的文章堆 <br> Iweidieng Iep's Article Heap](/@IID/IID-Heap-Home)

## 大眾向純技術類 Technical - for the Public
- [***簡報*** Etterna 與 Lua](/@IID/H11TbiFCm)

## 哲學類 Philosophy

## 評論 Commentary

## 雜記 Miscellaneous
- [***動畫*** 旋轉測試 Rotation Test](/@IID/rotation-test)

## 非大眾向純技術類 Technical - Not for the Public
- [***WIP | 英文*** Ψulang - 假想的多範型通用程式語言 A Fictitious Multi-Paradigm General-Purpose Programming Language](/@IID/SkcwPCPI8)

### Common TL Series
- [***中英對照*** Common TL Initial Table 通用臺羅拼音聲母列表](/@IID/Bk2VpvFqr)
- [***英文*** Common TL Phonetic notation system](/@IID/S1gG3ysGB)
- [Common TL（中文說明）](/@IID/BJIAKpczr)
- [***英文*** Common TL](/@IID/BJPwsU-0V)

###### Contact
- [<i class="fa fa-github"></i>@IepIweidieng](https://github.com/IepIweidieng) [target=_blank]
- [<i class="fa fa-codepen"></i>@IID](https://codepen.io/IID) [target=_blank]
- [<i class="fa fa-facebook-official"></i>@IepIweidieng](https://www.facebook.com/IepIweidieng) [target=_blank]
- [<i class="fa fa-envelope"></i>mail to me](mailto:iid@ccns.ncku.edu.tw) [target=_blank]