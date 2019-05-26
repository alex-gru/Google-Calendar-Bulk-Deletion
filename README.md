# Google-Calendar-Bulk-Deletion
Code snippet for in-browser bulk deletion of Google Calendar events

## Why you might need this script
* You imported events (e.g from an `.ics` file) into the wrong target calendar.
* You want to clean up your calendar
* You don't want to delete the events manually

## What this script does
It bulk deletes the list of calendar entries currently displayed.

## Limitations
The script does not handle additional confirm dialogs (e.g. for recurring events)

## What you have to do
Open Google Calendar, now `Search` for your target events you want to delete. Use the rich mask that Google Calendar offers here.

![](https://github.com/alex-gru/Google-Calendar-Bulk-Deletion/blob/master/search.jpg)

As soon as you verified that only those events are displayed, which you want to delete, open the developer tools via `F12` and paste the snippet into the console. Hit `ENTER` and watch the show 🍿.


## Demo

![](https://github.com/alex-gru/Google-Calendar-Bulk-Deletion/blob/master/demo.gif)


## The Snippet
Paste this snippet into your browser's console and hit `ENTER`.

```
bulkDelete();

function bulkDelete() {
	const list = Array.from(document.querySelectorAll('[role="main"] [role="rowgroup"] [role="presentation"]'));
	if (list.length === 0) return;
	list[0].click();
	setTimeout(() => {
		document.querySelector('[aria-label="Delete event"]').click();
		setTimeout(() => bulkDelete(), 500);
	}, 500);
}

```


