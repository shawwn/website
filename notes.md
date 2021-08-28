
# Table of Contents

1.  [org mode](#orgc8d1299)
    1.  [\`~/.emacs\` configuration for org mode](#orgb3a2db2)
    2.  [Tips](#org9d6c5a6)
        1.  [Insert a code block](#org0dc92bb)


<a id="orgc8d1299"></a>

# org mode

-   Tutorial: <https://orgmode.org/worg/org-tutorials/org4beginners.html>
-   Auto-export on save: <https://www.reddit.com/r/emacs/comments/4golh1/how_to_auto_export_html_when_saving_in_orgmode/>


<a id="orgb3a2db2"></a>

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


<a id="org9d6c5a6"></a>

## Tips


<a id="org0dc92bb"></a>

### Insert a code block

<https://emacs.stackexchange.com/questions/19945/command-to-insert-code-block>

\`(require 'org-tempo)\`, then \`<s\` followed by \`TAB\`.

