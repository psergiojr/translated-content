---
title: 例 3
slug: Learn/Forms/How_to_build_custom_form_controls/Example_3
l10n:
  sourceCommit: 741bc42293cb9a434367f5e998f5076a8ae8137e
original_slug: Learn/Forms/How_to_build_custom_form_widgets/Example_3
---

これは、[カスタムフォームウィジェットの作成方法](/ja/docs/Learn/Forms/How_to_build_custom_form_controls)を説明する 3 番目の例です。

## 状態を変更する

### HTML コンテンツ

```html
<form class="no-widget">
  <select name="myFruit" tabindex="-1">
      <option>Cherry</option>
      <option>Lemon</option>
      <option>Banana</option>
      <option>Strawberry</option>
      <option>Apple</option>
  </select>

  <div class="select" tabindex="0">
    <span class="value">Cherry</span>
    <ul class="optList hidden">
      <li class="option">Cherry</li>
      <li class="option">Lemon</li>
      <li class="option">Banana</li>
      <li class="option">Strawberry</li>
      <li class="option">Apple</li>
    </ul>
  </div>
</form>
```

### CSS コンテンツ

```css
.widget select,
.no-widget .select {
  position : absolute;
  left     : -5000em;
  height   : 0;
  overflow : hidden;
}

/* --------------- */
/* Required Styles */
/* --------------- */

.select {
  position: relative;
  display : inline-block;
}

.select.active,
.select:focus {
  box-shadow: 0 0 3px 1px #227755;
  outline: none;
}

.select .optList {
  position: absolute;
  top     : 100%;
  left    : 0;
}

.select .optList.hidden {
  max-height: 0;
  visibility: hidden;
}

/* ------------ */
/* Fancy Styles */
/* ------------ */

.select {
  font-size   : 0.625em; /* 10px */
  font-family : Verdana, Arial, sans-serif;

  box-sizing : border-box;

  padding : 0.1em 2.5em 0.2em 0.5em; /* 1px 25px 2px 5px */
  width   : 10em; /* 100px */

  border        : 0.2em solid #000; /* 2px */
  border-radius : 0.4em; /* 4px */

  box-shadow : 0 0.1em 0.2em rgba(0,0,0,.45); /* 0 1px 2px */

  background : #F0F0F0;
  background : linear-gradient(0deg, #E3E3E3, #fcfcfc 50%, #f0f0f0);
}

.select .value {
  display  : inline-block;
  width    : 100%;
  overflow : hidden;

  white-space   : nowrap;
  text-overflow : ellipsis;
  vertical-align: top;
}

.select:after {
  content : "▼";
  position: absolute;
  z-index : 1;
  height  : 100%;
  width   : 2em; /* 20px */
  top     : 0;
  right   : 0;

  padding-top : .1em;

  box-sizing : border-box;

  text-align : center;

  border-left  : .2em solid #000;
  border-radius: 0 .1em .1em 0;

  background-color : #000;
  color : #FFF;
}

.select .optList {
  z-index : 2;

  list-style: none;
  margin : 0;
  padding: 0;

  background: #f0f0f0;
  border: .2em solid #000;
  border-top-width : .1em;
  border-radius: 0 0 .4em .4em;

  box-shadow: 0 .2em .4em rgba(0,0,0,.4);

  box-sizing : border-box;

  min-width : 100%;
  max-height: 10em; /* 100px */
  overflow-y: auto;
  overflow-x: hidden;
}

.select .option {
  padding: .2em .3em;
}

.select .highlight {
  background: #000;
  color: #FFFFFF;
}
```

### JavaScript コンテンツ

```js
// -------------------- //
// Function definitions //
// -------------------- //

function deactivateSelect(select) {
  if (!select.classList.contains('active')) return;

  const optList = select.querySelector('.optList');

  optList.classList.add('hidden');
  select.classList.remove('active');
}

function activeSelect(select, selectList) {
  if (select.classList.contains('active')) return;

  selectList.forEach(deactivateSelect);
  select.classList.add('active');
};

function toggleOptList(select, show) {
  const optList = select.querySelector('.optList');

  optList.classList.toggle('hidden');
}

function highlightOption(select, option) {
  const optionList = select.querySelectorAll('.option');

  optionList.forEach((other) => {
    other.classList.remove('highlight');
  });

  option.classList.add('highlight');
};

// ------------- //
// Event binding //
// ------------- //

window.addEventListener("load", () => {
  const form = document.querySelector('form');

  form.classList.remove("no-widget");
  form.classList.add("widget");
});

window.addEventListener('load', () => {
  const selectList = document.querySelectorAll('.select');

  selectList.forEach((select) => {
    const optionList = select.querySelectorAll('.option');

    optionList.forEach((option) => {
      option.addEventListener('mouseover', () => {
        highlightOption(select, option);
      });
    });

    select.addEventListener('click', (event) => {
      toggleOptList(select);
    },  false);

    select.addEventListener('focus', (event) => {
      activeSelect(select, selectList);
    });

    select.addEventListener('blur', (event) => {
      deactivateSelect(select);
    });

    select.addEventListener('keyup', (event) => {
      if (event.keyCode === 27) {
        deactivateSelect(select);
      }
    });
  });
});
```

### 結果

{{ EmbedLiveSample('Change_states') }}