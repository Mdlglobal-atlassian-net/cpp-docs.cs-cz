---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 770e1d1c1cf288a7fe68f5bd076791d43f5b8572
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438910"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Poznámky

Tato možnost změní atributy oddílu a přepíše atributy, které byly nastaveny při kompilaci nebo propojení souboru objektu pro oddíl.

Za dvojtečku ( **:** ) zadejte *název* oddílu. Chcete-li změnit název oddílu, použijte *název* se symbolem rovná se (=) a *Nový_název* pro oddíl.

Chcete-li nastavit nebo změnit `attributes`oddílu, zadejte čárku ( **,** ) následovaný jedním nebo více znaky atributů. Pro negaci atributu, před jeho znak vykřičníkem (!). Následující znaky určují atributy paměti:

|Atribut|Nastavení|
|---------------|-------------|
|c|code|
|d|vypuštění|
|e|spouštěcí|
|Můžu|inicializovaná data|
|k|virtuální paměť v mezipaměti|
|m|odebrat odkaz|
|o|informace o propojení|
|p|stránkovaná virtuální paměť|
|r|read|
|s|shared|
|u|neinicializovaná data|
|w|write|

Chcete-li ovládací prvek *Zarovnání*, zadejte znak **a** následovaný jedním z následujících znaků pro nastavení velikosti zarovnání v bajtech následujícím způsobem:

|Znak|Velikost zarovnání v bajtech|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|bez zarovnání|

Zadejte `attributes` a *Zarovnání* znaků jako řetězec bez mezer. U znaků se nerozlišují malá a velká písmena.

## <a name="see-also"></a>Viz také

[EDITBIN – možnosti](editbin-options.md)
