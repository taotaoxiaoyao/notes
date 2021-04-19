# 虚拟DOM
## 什么是虚拟DOM
> 使用普通的Javascript对象描述真实的DOM
```html
<div id="nav"></div>
```
```js
const nav = document.querySelector('#nav')
let real = ''
for(let i in nav) {
    real += i + ','
}
console.log(real)
```
打印真实DOM如下：
```js
align,title,lang,translate,dir,hidden,accessKey,draggable,spellcheck,autocapitalize,contentEditable,isContentEditable,inputMode,offsetParent,offsetTop,offsetLeft,offsetWidth,offsetHeight,style,innerText,outerText,onabort,onblur,oncancel,oncanplay,oncanplaythrough,onchange,onclick,onclose,oncontextmenu,oncuechange,ondblclick,ondrag,ondragend,ondragenter,ondragleave,ondragover,ondragstart,ondrop,ondurationchange,onemptied,onended,onerror,onfocus,onformdata,oninput,oninvalid,onkeydown,onkeypress,onkeyup,onload,onloadeddata,onloadedmetadata,onloadstart,onmousedown,onmouseenter,onmouseleave,onmousemove,onmouseout,onmouseover,onmouseup,onmousewheel,onpause,onplay,onplaying,onprogress,onratechange,onreset,onresize,onscroll,onseeked,onseeking,onselect,onstalled,onsubmit,onsuspend,ontimeupdate,ontoggle,onvolumechange,onwaiting,onwebkitanimationend,onwebkitanimationiteration,onwebkitanimationstart,onwebkittransitionend,onwheel,onauxclick,ongotpointercapture,onlostpointercapture,onpointerdown,onpointermove,onpointerup,onpointercancel,onpointerover,onpointerout,onpointerenter,onpointerleave,onselectstart,onselectionchange,onanimationend,onanimationiteration,onanimationstart,ontransitionrun,ontransitionstart,ontransitionend,ontransitioncancel,oncopy,oncut,onpaste,dataset,nonce,autofocus,tabIndex,attachInternals,blur,click,focus,onpointerrawupdate,enterKeyHint,namespaceURI,prefix,localName,tagName,id,className,classList,slot,attributes,shadowRoot,part,assignedSlot,innerHTML,outerHTML,scrollTop,scrollLeft,scrollWidth,scrollHeight,clientTop,clientLeft,clientWidth,clientHeight,attributeStyleMap,onbeforecopy,onbeforecut,onbeforepaste,onsearch,elementTiming,onfullscreenchange,onfullscreenerror,onwebkitfullscreenchange,onwebkitfullscreenerror,onbeforexrselect,children,firstElementChild,lastElementChild,childElementCount,previousElementSibling,nextElementSibling,after,animate,append,attachShadow,before,closest,computedStyleMap,getAttribute,getAttributeNS,getAttributeNames,getAttributeNode,getAttributeNodeNS,getBoundingClientRect,getClientRects,getElementsByClassName,getElementsByTagName,getElementsByTagNameNS,hasAttribute,hasAttributeNS,hasAttributes,hasPointerCapture,insertAdjacentElement,insertAdjacentHTML,insertAdjacentText,matches,prepend,querySelector,querySelectorAll,releasePointerCapture,remove,removeAttribute,removeAttributeNS,removeAttributeNode,replaceWith,requestFullscreen,requestPointerLock,scroll,scrollBy,scrollIntoView,scrollIntoViewIfNeeded,scrollTo,setAttribute,setAttributeNS,setAttributeNode,setAttributeNodeNS,setPointerCapture,toggleAttribute,webkitMatchesSelector,webkitRequestFullScreen,webkitRequestFullscreen,ariaAtomic,ariaAutoComplete,ariaBusy,ariaChecked,ariaColCount,ariaColIndex,ariaColSpan,ariaCurrent,ariaDescription,ariaDisabled,ariaExpanded,ariaHasPopup,ariaHidden,ariaKeyShortcuts,ariaLabel,ariaLevel,ariaLive,ariaModal,ariaMultiLine,ariaMultiSelectable,ariaOrientation,ariaPlaceholder,ariaPosInSet,ariaPressed,ariaReadOnly,ariaRelevant,ariaRequired,ariaRoleDescription,ariaRowCount,ariaRowIndex,ariaRowSpan,ariaSelected,ariaSetSize,ariaSort,ariaValueMax,ariaValueMin,ariaValueNow,ariaValueText,getAnimations,replaceChildren,nodeType,nodeName,baseURI,isConnected,ownerDocument,parentNode,parentElement,childNodes,firstChild,lastChild,previousSibling,nextSibling,nodeValue,textContent,ELEMENT_NODE,ATTRIBUTE_NODE,TEXT_NODE,CDATA_SECTION_NODE,ENTITY_REFERENCE_NODE,ENTITY_NODE,PROCESSING_INSTRUCTION_NODE,COMMENT_NODE,DOCUMENT_NODE,DOCUMENT_TYPE_NODE,DOCUMENT_FRAGMENT_NODE,NOTATION_NODE,DOCUMENT_POSITION_DISCONNECTED,DOCUMENT_POSITION_PRECEDING,DOCUMENT_POSITION_FOLLOWING,DOCUMENT_POSITION_CONTAINS,DOCUMENT_POSITION_CONTAINED_BY,DOCUMENT_POSITION_IMPLEMENTATION_SPECIFIC,appendChild,cloneNode,compareDocumentPosition,contains,getRootNode,hasChildNodes,insertBefore,isDefaultNamespace,isEqualNode,isSameNode,lookupNamespaceURI,lookupPrefix,normalize,removeChild,replaceChild,addEventListener,dispatchEvent,removeEventListener,
```
使用虚拟DOM描述真实DOM如下：

  ```js
  {
    sel: "div",
    data: {},
    children: undefined,
    text: "Hello Virtual DOM",
    elm: undefined,
    key: undefined
  }
  ```