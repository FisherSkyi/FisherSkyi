## About me

a student.

```js
window.addEventListener('load', function () {
  loadComments();
})

let tryAttempts = 0;

function loadComments () {
	let needRescheduling = false;
	const buttons = document.querySelectorAll(".ajax-pagination-btn[data-disable-with]")
	
	buttons.forEach((button) => {
		button.click();
		needRescheduling = true;
		tryAttempts = 0;
	})
	
	if (needRescheduling || tryAttempts < 5) {
		if (needRescheduling) {
			console.log("Loading comments.")
		} else {
			console.log("Looking for more to load.");
		}
		tryAttempts++;
		setTimeout(loadComments, 500)
	} else {
		console.log("All comments loaded.");

		const resolvedButtons = document.querySelectorAll(".js-toggle-outdated-comments[data-view-component]");

		resolvedButtons.forEach((button) => {
			button.click();
		})
		
		console.log("All resolved comments loaded.")
	}
}
```

source: https://github.com/refined-github/refined-github/issues/1892#issuecomment-1044913449
