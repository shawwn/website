
# Table of Contents

1.  [twitter](#org6597456)
    1.  [Find the most liked tweets from an account](#orgee0f018)
        1.  [@theshawwn's most favorited tweets](#orgc29b848)
2.  [org mode](#org2277a22)
    1.  [Org Mode Tutorial](#orgd26d20d)
    2.  [\`~/.emacs\` configuration for org mode](#orgd7f4169)
    3.  [Auto-export on save](#orgea8a5fc)
    4.  [Insert a code block](#orgca98dea)
    5.  [Insert Hyperlinks](#org679b2f5)
    6.  [Getting Things Done (GTD) workflow](#org2cfa121)
    7.  [Export all headlines in ToC](#orgbd39b0b)
        1.  [See also](#orgab05fe7)
3.  [misc](#orge1719c8)
    1.  [deeply](#orgcb19e06)
        1.  [nested](#org14dfc1c)
            1.  [deeply](#org78ce44c)
                1.  [nested](#org8b658e8)
                    1.  [deeply](#orgeebe292)



<a id="org6597456"></a>

# twitter


<a id="orgee0f018"></a>

## Find the most liked tweets from an account

<https://webapps.stackexchange.com/questions/105958/find-the-most-liked-tweet-from-an-account>


<a id="orgc29b848"></a>

### @theshawwn's most favorited tweets

<https://twitter.com/search?q=from%3Atheshawwn%20min_faves%3A60&src=typed_query&f=live>


<a id="org2277a22"></a>

# org mode


<a id="orgd26d20d"></a>

## Org Mode Tutorial

<https://orgmode.org/worg/org-tutorials/org4beginners.html>


<a id="orgd7f4169"></a>

## \`~/.emacs\` configuration for org mode

    ;------------------------------------------------------------
    ; org mode
    ; https://orgmode.org/worg/org-tutorials/org4beginners.html#org9825076
    ;------------------------------------------------------------
    
    ;; Enable transient mark mode
    (transient-mark-mode 1)
    
    ;;;;Org mode configuration
    ;; Enable Org mode
    (require 'org)
    ;; Make Org mode work with files ending in .org
    ;; (add-to-list 'auto-mode-alist '("\\.org$" . org-mode))
    ;; The above is the default in recent emacsen
    
    
    ;; https://www.reddit.com/r/emacs/comments/4golh1/how_to_auto_export_html_when_saving_in_orgmode/
    (defun toggle-org-markdown-export-on-save ()
      (interactive)
      (if (memq 'org-md-export-to-markdown after-save-hook)
          (progn
            (remove-hook 'after-save-hook 'org-md-export-to-markdown t)
            (message "Disabled org markdown export on save for current buffer..."))
        (add-hook 'after-save-hook 'org-md-export-to-markdown nil t)
        (message "Enabled org markdown export on save for current buffer...")))
    
    
    (add-hook 'org-mode-hook #'toggle-org-markdown-export-on-save)
    
    ;; https://emacs.stackexchange.com/questions/19945/command-to-insert-code-block
    ;; <s then TAB
    (require 'org-tempo)


<a id="orgea8a5fc"></a>

## Auto-export on save

<https://www.reddit.com/r/emacs/comments/4golh1/how_to_auto_export_html_when_saving_in_orgmode/>


<a id="orgca98dea"></a>

## Insert a code block

<https://emacs.stackexchange.com/questions/19945/command-to-insert-code-block>

    (require 'org-tempo)
    ;; then type <s followed by TAB


<a id="org679b2f5"></a>

## Insert Hyperlinks

<https://orgmode.org/guide/Hyperlinks.html>

    [[example.com][Example]]


<a id="org2cfa121"></a>

## Getting Things Done (GTD) workflow

<http://members.optusnet.com.au/~charles57/GTD/gtd_workflow.html>


<a id="orgbd39b0b"></a>

## Export all headlines in ToC

Usually org-mode only exports up to 3 nestings deep. To export all headlines, no matter how deeply, add this to the top of the org file:

    #+OPTIONS: H:10


<a id="orgab05fe7"></a>

### See also

-   [Export Settings](https://orgmode.org/manual/Export-Settings.html)
-   [Markdown Export](https://orgmode.org/manual/Markdown-Export.html)


<a id="orge1719c8"></a>

# misc


<a id="orgcb19e06"></a>

## deeply

Deeply nested ToC test


<a id="org14dfc1c"></a>

### nested

Deeply nested ToC test


<a id="org78ce44c"></a>

#### deeply

Deeply nested ToC test


<a id="org8b658e8"></a>

##### nested

Deeply nested ToC test


<a id="orgeebe292"></a>

###### deeply

Deeply nested ToC test

