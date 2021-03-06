# Scrub

Scrubbing away unwanted browser history

### URL Remover

There are varoius reasons when or why one may use incognito, for example you may want to safely search for a birthday present for your loved one without worrying if they'll be able to see remnants of what you've looked up. However sometimes you may want to preserve most of your user history, while just removing sites that contain specific keywords. This chrome extension will replace the need to use incogntido, and provide users with the ability of blacklisting keywords or sites that will automatically be deleted on a new page load.




### Functionality & MVP

With this extension, users will be able to:

- [ ] Input into a form specific urls or keywords to be blacklisted
- [ ] Deletes from Browser any urls that are on the blacklist
- [ ] Removes keywords from Scrub list 


#How to use

  - In the Scrub input field type in any text you believe is associated  with URLs that you'd like to remove. The extension will then remove those URLs from your history. Any text that is inputed into the Scrub input box will persist, as text are added to a list that will be checked and removed from the history on page load.

- In the Un-Scrub input field type in a keyword that you'd like to be removed from the Scrub list, and the removal of that keyword from URL history will no longer persist.


### Scrub in Action

#![Scrub in Action](https://github.com/ac7552/Scrub/blob/master/Yank_in_action.png)
#![Chrome History 1] (https://github.com/ac7552/Scrub/blob/master/chrome_history1.png)
#![Chrome History 2] (https://github.com/ac7552/Scrub/blob/master/chrome_history2.png)

### Technologies & Technical Challenges

This extension will be implemented using the standard Chrome extension technology: Javascript, HTML, and CSS.  In addition to the `manifest.json` and `package.json` files, there will be two scripts:

- `content.js`: will contain the logic for finding urls or keywords matching those on the blacklist
- `options.js`: will contain the logic for changing the user's settings

There will also be two HTML files to display the content:

- `new_style.css`: the file containing the styling rules for the form
- `options.html`: the file that renders the Settings menu for the user

This app also makes extensive use of the chrome history api: 
https://developer.chrome.com/extensions/history

#Code Snippet:
  - How Scrub removes URLs from Chrome History
````Javascript

let itemsDelete = () => {
  for(let i = 0; i < URL_LIST.length ; i++ ){
    chrome.history.search({text: URL_LIST[i]}, function(data){
    for(let i = 0; i < Object.keys(data).length; i++){
       chrome.history.deleteUrl({url: data[i].url})
     }
   });
  }
}

````

<!-- ### Implementation Timeline

**Day 1**: Get started on the infrastructure of the extension, following <a href="https://developer.chrome.com/extensions/getstarted">this guide</a> from Chrome.  By the end of the day, I will have:

- A completed `package.json`
- A completed `manifest.json`
- The ability to input keywords and urls to be blacklisted

**Day 2**: Work on identifying urls that match those that have been blacklisted
using https://developer.chrome.com/extensions/history
- Removes blacklisted urls
- Removes urls that contain keywords matching those that have blacklisted

**Day 3**: Dedicate this day to polishing Day 2 work

- Upon successful exit of the browser blacklisted items are deleted
- Present new options for blacklisting upon entering a fresh browser

**Day 4**: Polish and refactored code  -->
