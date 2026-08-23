# Integrazione Shopify Buy Button — Kombucha Gula Fit (SELEZIONE Kelua)

Istruzioni per Claude Code: integrare questi 4 Buy Button nella sezione prodotti del sito kelua.it, mantenendo esattamente il design/layout attuale del sito. Ogni bottone va inserito nella card del prodotto corrispondente (stesso ordine/nome usato in schede-prodotto-gulafit-kelua.md).

Tutti i bottoni sono già stilizzati coerenti col brand: sfondo terracotta `#d5a98b`, hover `#c0987d`, font Avant Garde. Non modificare questi colori, sono già allineati alla palette del sito (--cta / --cta-hover).

Ogni prodotto è **preorder**: la merce non è ancora fisicamente disponibile. Aggiungere sopra o accanto a ciascun Buy Button un badge/testo:

**"Preordine — spedizione prevista entro il 15 ottobre 2026"**

(stile badge coerente col design esistente, es. piccolo tag in Salvia `#7F8A75` con testo Crema `#F7F3EE`, o come preferisce il sistema di design del sito).

---

## 1. Kombucha Ananas e Menta

```html
<div id='product-component-1787502139122'></div>
<script type="text/javascript">
/*<![CDATA[*/
(function () {
  var scriptURL = 'https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js';
  if (window.ShopifyBuy) {
    if (window.ShopifyBuy.UI) {
      ShopifyBuyInit();
    } else {
      loadScript();
    }
  } else {
    loadScript();
  }
  function loadScript() {
    var script = document.createElement('script');
    script.async = true;
    script.src = scriptURL;
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(script);
    script.onload = ShopifyBuyInit;
  }
  function ShopifyBuyInit() {
    var client = ShopifyBuy.buildClient({
      domain: 'kcinyb-um.myshopify.com',
      storefrontAccessToken: '2d7451e82aee49e9e68c5a145fa7e919',
    });
    ShopifyBuy.UI.onReady(client).then(function (ui) {
      ui.createComponent('product', {
        id: '10221186580808',
        node: document.getElementById('product-component-1787502139122'),
        moneyFormat: '%E2%82%AC%7B%7Bamount_with_comma_separator%7D%7D',
        options: {
  "product": {
    "styles": {
      "product": {
        "@media (min-width: 601px)": {
          "max-width": "calc(25% - 20px)",
          "margin-left": "20px",
          "margin-bottom": "50px"
        }
      },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "productSet": {
    "styles": { "products": { "@media (min-width: 601px)": { "margin-left": "-20px" } } }
  },
  "modalProduct": {
    "contents": { "img": false, "imgWithCarousel": true, "button": false, "buttonWithQuantity": true },
    "styles": {
      "product": { "@media (min-width: 601px)": { "max-width": "100%", "margin-left": "0px", "margin-bottom": "0px" } },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "option": {},
  "cart": {
    "styles": {
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "total": "Subtotal", "button": "Checkout" }
  },
  "toggle": {
    "styles": {
      "toggle": {
        "font-family": "Avant Garde, sans-serif",
        "background-color": "#d5a98b",
        ":hover": { "background-color": "#c0987d" },
        ":focus": { "background-color": "#c0987d" }
      }
    }
  }
},
      });
    });
  }
})();
/*]]>*/
</script>
```

---

## 2. Kombucha Fragola e Lime

```html
<div id='product-component-1787502306750'></div>
<script type="text/javascript">
/*<![CDATA[*/
(function () {
  var scriptURL = 'https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js';
  if (window.ShopifyBuy) {
    if (window.ShopifyBuy.UI) {
      ShopifyBuyInit();
    } else {
      loadScript();
    }
  } else {
    loadScript();
  }
  function loadScript() {
    var script = document.createElement('script');
    script.async = true;
    script.src = scriptURL;
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(script);
    script.onload = ShopifyBuyInit;
  }
  function ShopifyBuyInit() {
    var client = ShopifyBuy.buildClient({
      domain: 'kcinyb-um.myshopify.com',
      storefrontAccessToken: '2d7451e82aee49e9e68c5a145fa7e919',
    });
    ShopifyBuy.UI.onReady(client).then(function (ui) {
      ui.createComponent('product', {
        id: '10221186842952',
        node: document.getElementById('product-component-1787502306750'),
        moneyFormat: '%E2%82%AC%7B%7Bamount_with_comma_separator%7D%7D',
        options: {
  "product": {
    "styles": {
      "product": {
        "@media (min-width: 601px)": {
          "max-width": "calc(25% - 20px)",
          "margin-left": "20px",
          "margin-bottom": "50px"
        }
      },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "productSet": {
    "styles": { "products": { "@media (min-width: 601px)": { "margin-left": "-20px" } } }
  },
  "modalProduct": {
    "contents": { "img": false, "imgWithCarousel": true, "button": false, "buttonWithQuantity": true },
    "styles": {
      "product": { "@media (min-width: 601px)": { "max-width": "100%", "margin-left": "0px", "margin-bottom": "0px" } },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "option": {},
  "cart": {
    "styles": {
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "total": "Subtotal", "button": "Checkout" }
  },
  "toggle": {
    "styles": {
      "toggle": {
        "font-family": "Avant Garde, sans-serif",
        "background-color": "#d5a98b",
        ":hover": { "background-color": "#c0987d" },
        ":focus": { "background-color": "#c0987d" }
      }
    }
  }
},
      });
    });
  }
})();
/*]]>*/
</script>
```

---

## 3. Kombucha Mandarino e Ibisco

```html
<div id='product-component-1787502384746'></div>
<script type="text/javascript">
/*<![CDATA[*/
(function () {
  var scriptURL = 'https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js';
  if (window.ShopifyBuy) {
    if (window.ShopifyBuy.UI) {
      ShopifyBuyInit();
    } else {
      loadScript();
    }
  } else {
    loadScript();
  }
  function loadScript() {
    var script = document.createElement('script');
    script.async = true;
    script.src = scriptURL;
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(script);
    script.onload = ShopifyBuyInit;
  }
  function ShopifyBuyInit() {
    var client = ShopifyBuy.buildClient({
      domain: 'kcinyb-um.myshopify.com',
      storefrontAccessToken: '2d7451e82aee49e9e68c5a145fa7e919',
    });
    ShopifyBuy.UI.onReady(client).then(function (ui) {
      ui.createComponent('product', {
        id: '10221187662152',
        node: document.getElementById('product-component-1787502384746'),
        moneyFormat: '%E2%82%AC%7B%7Bamount_with_comma_separator%7D%7D',
        options: {
  "product": {
    "styles": {
      "product": {
        "@media (min-width: 601px)": {
          "max-width": "calc(25% - 20px)",
          "margin-left": "20px",
          "margin-bottom": "50px"
        }
      },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "productSet": {
    "styles": { "products": { "@media (min-width: 601px)": { "margin-left": "-20px" } } }
  },
  "modalProduct": {
    "contents": { "img": false, "imgWithCarousel": true, "button": false, "buttonWithQuantity": true },
    "styles": {
      "product": { "@media (min-width: 601px)": { "max-width": "100%", "margin-left": "0px", "margin-bottom": "0px" } },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "option": {},
  "cart": {
    "styles": {
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "total": "Subtotal", "button": "Checkout" }
  },
  "toggle": {
    "styles": {
      "toggle": {
        "font-family": "Avant Garde, sans-serif",
        "background-color": "#d5a98b",
        ":hover": { "background-color": "#c0987d" },
        ":focus": { "background-color": "#c0987d" }
      }
    }
  }
},
      });
    });
  }
})();
/*]]>*/
</script>
```

---

## 4. Kombucha Pitaya e Maracujà

```html
<div id='product-component-1787502406580'></div>
<script type="text/javascript">
/*<![CDATA[*/
(function () {
  var scriptURL = 'https://sdks.shopifycdn.com/buy-button/latest/buy-button-storefront.min.js';
  if (window.ShopifyBuy) {
    if (window.ShopifyBuy.UI) {
      ShopifyBuyInit();
    } else {
      loadScript();
    }
  } else {
    loadScript();
  }
  function loadScript() {
    var script = document.createElement('script');
    script.async = true;
    script.src = scriptURL;
    (document.getElementsByTagName('head')[0] || document.getElementsByTagName('body')[0]).appendChild(script);
    script.onload = ShopifyBuyInit;
  }
  function ShopifyBuyInit() {
    var client = ShopifyBuy.buildClient({
      domain: 'kcinyb-um.myshopify.com',
      storefrontAccessToken: '2d7451e82aee49e9e68c5a145fa7e919',
    });
    ShopifyBuy.UI.onReady(client).then(function (ui) {
      ui.createComponent('product', {
        id: '10221187432776',
        node: document.getElementById('product-component-1787502406580'),
        moneyFormat: '%E2%82%AC%7B%7Bamount_with_comma_separator%7D%7D',
        options: {
  "product": {
    "styles": {
      "product": {
        "@media (min-width: 601px)": {
          "max-width": "calc(25% - 20px)",
          "margin-left": "20px",
          "margin-bottom": "50px"
        }
      },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "productSet": {
    "styles": { "products": { "@media (min-width: 601px)": { "margin-left": "-20px" } } }
  },
  "modalProduct": {
    "contents": { "img": false, "imgWithCarousel": true, "button": false, "buttonWithQuantity": true },
    "styles": {
      "product": { "@media (min-width: 601px)": { "max-width": "100%", "margin-left": "0px", "margin-bottom": "0px" } },
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "button": "Add to cart" }
  },
  "option": {},
  "cart": {
    "styles": {
      "button": {
        "font-family": "Avant Garde, sans-serif",
        ":hover": { "background-color": "#c0987d" },
        "background-color": "#d5a98b",
        ":focus": { "background-color": "#c0987d" }
      }
    },
    "text": { "total": "Subtotal", "button": "Checkout" }
  },
  "toggle": {
    "styles": {
      "toggle": {
        "font-family": "Avant Garde, sans-serif",
        "background-color": "#d5a98b",
        ":hover": { "background-color": "#c0987d" },
        ":focus": { "background-color": "#c0987d" }
      }
    }
  }
},
      });
    });
  }
})();
/*]]>*/
</script>
```

---

## Checklist per Claude Code

- [ ] Ogni Buy Button va nella card del prodotto corrispondente (usare `schede-prodotto-gulafit-kelua.md` per testi/immagini/ordine)
- [ ] Aggiungere badge "Preordine — spedizione prevista entro il 15 ottobre 2026" su ciascuna card, stile coerente col design system esistente
- [ ] Non modificare i colori del bottone (già allineati a --cta / --cta-hover del sito)
- [ ] Il checkout Shopify è configurato per aprirsi in popup, non serve gestire redirect
- [ ] Verificare che lo script Shopify SDK non venga caricato 4 volte se i 4 bottoni sono nella stessa pagina (valutare caricamento singolo condiviso se necessario per performance)
