---
title: Reader Theme
description: Customized Medium style markdown css. Based on `@yukai/medium-theme`
tags: theme
original-TODOs:
    - revisit heading from h1~h6
    - Screenshot
    - alternative blockquote style
    - tables
CHANGEs:
    - Prevent emoji from being centered
    - Only styling `alert-info` without additional classes
    - Remove replicated rules to simplify the code
    - Disable the rule for the largest text size to make it fit the UI more
    - Use `text-indent` to hide `tags:` to deal with line wraps
    - Apply the font setting to everything
---

<style>
.markdown-body img:not(.emoji) + strong {
    display: block; 
    text-align: center;
    font-weight: normal;
    margin-top: 10px;
    color: rgba(0, 0, 0, 0.54);
    font-size: 16px;
}

.markdown-body [class="alert alert-info part"] {
    background: rgba(0, 0, 0, 0.05);
    border: none;
    border-radius: 0px;
    font-size: 16px;
}

.markdown-body [class="alert alert-info part"] p {
    font-family: Menlo, Monaco, "Courier New", Courier, monospace;
    /* white-space: pre-wrap; */ /* Disable if hard breaks are enabled */
}

.markdown-body blockquote {
    font-family: 'Noto Serif TC', medium-content-serif-font, Georgia, Cambria, "Times New Roman", Times, serif;
    padding-left: 30px;
    border: none;
    font-size: 30px;
    font-weight: 400;
    letter-spacing: -0.014em;
    line-height: 1.48;
}

.markdown-body hr {
    background-color: transparent;
    height: auto;
    text-align: center;
    font-size: 28px;
    margin-left: auto;
    margin-right: auto;
    margin: 24px 0 32px;
}

.markdown-body hr:before {
    content: "...";
    line-height: 1.4;
    font-style: italic;
    text-indent: 0.6em;
    letter-spacing: 0.6em;
}


.markdown-body blockquote p {
    color: rgba(0, 0, 0, 0.54);
}

/* centered image */
.markdown-body img:not(.emoji) {
    display: block;
    margin-left: auto;
    margin-right: auto;
}

.markdown-body h1 {
    font-size: 40px;
    border: none;
}

.markdown-body h2 {
    border: none;
}

.markdown-body h1:first-child + h2 {
    color: rgba(0, 0, 0, 0.54);
    margin-top: -28px;
    font-weight: 300;
    font-size: 24px;
}

.markdown-body h6[id^="tags"] {
    font-size: 0;
    color: transparent;
}

.markdown-body h6[id^="tags"] > a, 
.markdown-body h6[id^="tags"] > code { 
    font-size: 15px;
    color: rgba(0, 0, 0, 0.54) !important;
}
.markdown-body h6[id^="tags"] > code {
    font-family: medium-content-sans-serif-font, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    padding: 5px 10px;
}

.markdown-body p {
    font-family: 'Noto Serif TC', medium-content-serif-font, Georgia, Cambria, "Times New Roman", Times, serif;
    line-height: 1.58;
    color: rgba(0, 0, 0, 0.84);
}

.markdown-body p, .markdown-body blockquote, .markdown-body ul, .markdown-body ol, .markdown-body dl, .markdown-body table, .markdown-body pre {
    margin-bottom: 2em;
}

.markdown-body > ol, .markdown-body > ul {
    font-family: 'Noto Serif TC', medium-content-serif-font, Georgia, Cambria, "Times New Roman", Times, serif;
    color: rgba(0, 0, 0, 0.84);
}

.markdown-body > table {
    font-size: 16px;
}

@media screen /* and (max-width: 727.98px) */ and (min-width: 552px) {
    .markdown-body {
        font-size: 18px;
    }
    
    .markdown-body h2 {
        font-size: 24px;
    }
    
    .markdown-body p > img:not(.emoji) {
        margin-top: 20px;
    }
}
/*
@media screen and (min-width: 728px) {
    .markdown-body {
        font-size: 21px;
    }
    
    .markdown-body h2 {
        font-size: 26px;
    }

    .markdown-body p > img:not(.emoji) {
        margin-top: 36px;
    }
}
*/

#doc.markdown-body {
    font-family: medium-content-sans-serif-font, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
    padding-left: 24px;
    padding-right: 24px;
    
    width: 100%;
}

.markdown-body pre > code {
    font-size: 15px;
}


.markdown-body > p > img:not(.emoji) {
    max-width: calc(1032px);
    position: relative;
    margin-left: 50%;
    transform: translateX(-50%);
}

@media screen and (max-width: 1079.98px) {
    .markdown-body > p > img:not(.emoji) {
        max-width: 100%;
        transform: unset;
        margin-left: auto;
        margin-right: auto;
    }
}

body > #ui-toc-affix {
    display: none !important;
}

html[lang] > body[style] {
    font-family: medium-content-sans-serif-font, -apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Oxygen, Ubuntu, Cantarell, "Open Sans", "Helvetica Neue", sans-serif;
}

.markdown-body a,  .markdown-body a:hover, .markdown-body a:active {
    text-decoration: underline;
    color: inherit;
}

</style>

