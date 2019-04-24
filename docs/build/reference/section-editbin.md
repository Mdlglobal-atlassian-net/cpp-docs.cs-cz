---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 8bcc925b34118630c872a0147b93291626b7c19b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318599"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Poznámky

Tato možnost změní atributy oddílu a přepíše přitom atributy nastavené při kompilaci nebo propojené souboru objektu pro oddíl.

Za dvojtečkou ( **:** ), zadejte *název* oddílu. Chcete-li změnit název oddílu, postupujte podle *název* znaménkem rovná se (=) a *newname* pro oddíl.

Nastavit nebo změnit v části `attributes`, zadejte čárku (**,**) následované znaky jeden nebo více atributů. Chcete-li negate – atribut, před jeho znak s vykřičníkem (!). Tyto znaky zadat atributy paměti:

|Atribut|Nastavení|
|---------------|-------------|
|c|kód|
|d|Discardable|
|e|spustitelný soubor|
|Mohu|inicializovaná data|
|k|v mezipaměti virtuální paměti|
|m|Odebrat odkaz|
|o|informace o propojení|
|p|stránkovaná virtuální paměť|
|r|read|
|s|shared|
|u|Neinicializovaná data|
|w|write|

Ovládací prvek *zarovnání*, zadejte znak **A** , následovaný jednou z následujících znaků nastavit velikost zarovnání v bajtech, následujícím způsobem:

|Znak|Zarovnání velikost v bajtech|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|bez zarovnání|

Zadejte `attributes` a *zarovnání* znaků jako řetězec s žádné prázdné znaky. Znaky nejsou velká a malá písmena.

## <a name="see-also"></a>Viz také:

[EDITBIN – možnosti](editbin-options.md)
