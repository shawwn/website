
# Table of Contents

1.  [twitter](#orgf68af1d)
    1.  [Find the most liked tweets from an account](#orge998b58)
        1.  [@theshawwn's most favorited tweets](#org3f6cb76)
2.  [org mode](#org2ab0d9d)
    1.  [notes](#org3255d6c)
    2.  [\`~/.emacs\` configuration for org mode](#orgbdd8288)
    3.  [Tips](#orgb16c1c3)
        1.  [Insert a code block](#org3f06aa2)


<a id="orgf68af1d"></a>

# twitter


<a id="orge998b58"></a>

## Find the most liked tweets from an account

<https://webapps.stackexchange.com/questions/105958/find-the-most-liked-tweet-from-an-account>


<a id="org3f6cb76"></a>

### @theshawwn's most favorited tweets

<https://twitter.com/search?q=from%3Atheshawwn%20min_faves%3A60&src=typed_query&f=live>


<a id="org2ab0d9d"></a>

# org mode


<a id="org3255d6c"></a>

## notes

-   Tutorial: <https://orgmode.org/worg/org-tutorials/org4beginners.html>
    -   Getting Things Done (GTD) workflow: <http://members.optusnet.com.au/~charles57/GTD/gtd_workflow.html>
-   Auto-export on save: <https://www.reddit.com/r/emacs/comments/4golh1/how_to_auto_export_html_when_saving_in_orgmode/>


<a id="orgbdd8288"></a>

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


<a id="orgb16c1c3"></a>

## Tips


<a id="org3f06aa2"></a>

### Insert a code block

<https://emacs.stackexchange.com/questions/19945/command-to-insert-code-block>

