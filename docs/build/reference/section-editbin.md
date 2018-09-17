---
title: -SECTION (EDITBIN) | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /section
dev_langs:
- C++
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 3f91d467681d5a4d5bf4eaa5f042ef44b87810b3
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2018
ms.locfileid: "45701975"
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
|TIS.|v mezipaměti virtuální paměti|
|m|Odebrat odkaz|
|O|informace o propojení|
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

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](../../build/reference/editbin-options.md)