---
title: Chyba kompilátoru prostředků RW2003
ms.date: 11/04/2016
f1_keywords:
- RW2003
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
ms.openlocfilehash: 60e813fff46ebc015f281dfed99d2916ca0eb4bb
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/24/2020
ms.locfileid: "80190609"
---
# <a name="resource-compiler-error-rw2003"></a>Chyba kompilátoru prostředků RW2003

Chyba generování

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Opravu provedete kontrolou následujících možných příčin.

1. **Chyba: prostředek souboru rastrového obrázku – soubor není ve formátu 3,00.**

   Rastrové obrázky používající formát Windows verze 2. x nelze použít ve zdrojových souborech verze 3. x. Rastrový obrázek musí být překreslen nebo převeden na 3. x formát.

1. **Chyba: stará DIB v názvu prostředku. Předání přes SDKPAINT**

   Rastrový obrázek nezávislý na zařízení (DIB) v zadaném prostředku není kompatibilní s formátem Windows 3,0. Rastrový obrázek musí být překreslen nebo převeden na formát 3. x.

1. **Chyba: prostředek souboru prostředků – název není ve formátu 3,00.**

   Ikona nebo kurzor v zadaném prostředku používal formát z předchozí verze Windows. Ikona nebo kurzor musí být překresleny nebo převedeny na formát 3. x.

1. **Neznámý formát hlavičky DIB**

   Záhlaví rastrového obrázku není struktura BITMAPCOREHEADER nebo BITMAPINFOHEADER.

1. **Nepovedlo se inicializovat informace o symbolech.**

   K této chybě dochází pouze v C++jazyce Visual. Pravděpodobnou příčinou je, že máte příliš mnoho otevřených souborů, nebo nemůžete otevřít nebo zapsat do datových souborů potřebných pro vizuál C++ import symbolů do skriptu. Vizuál C++ se pokusí vytvořit tyto soubory v adresáři určeném proměnnou prostředí **TMP** nebo aktuálním adresářem, pokud není zadaný žádný.

1. **Nepovedlo se uložit informace o symbolech.**

   K této chybě dochází pouze v C++jazyce Visual. Pravděpodobnou příčinou je, že máte příliš mnoho otevřených souborů, nebo nemůžete zavřít nebo zapsat do datových souborů potřebných pro vizuál C++ import symbolů do skriptu. Vizuál C++ se pokusí použít tyto soubory v adresáři určeném proměnnou prostředí **TMP** nebo aktuálním adresářem, pokud není zadaný žádný.

1. **Soubor prostředků rastrového souboru není ve formátu 2,03.**

   Rastrový obrázek používal formát starší verze než 2,03. Rastrový obrázek musí být převeden nebo překreslen pomocí formátu verze 3,00 nebo novější.

1. **Prostředek je moc velký.**

   Pro systém Windows 3,1 může prostředek překročit přibližně 65000 bajtů. Pokud je váš prostředek, pak ho nebude možné zkompilovat pomocí vizuálu C++ nebo kompilátoru prostředků příkazového řádku. Toto omezení se nevztahuje na kurzory, ikony, rastrové obrázky ani jiné souborové prostředky.

1. **Soubor prostředků není ve formátu 3,00.**

   Kurzor nebo ikona používaly formát starší verze než 3,00. Prostředek musí být převeden nebo překreslen pomocí formátu verze 3,00 nebo novější.

1. **Nepovedlo se otevřít dočasný soubor.**

   Kompilátor prostředků nebo vizuál C++ nemohl otevřít dočasný soubor. Pravděpodobnou příčinou je, že nemáte oprávnění k zápisu do adresáře nebo že adresář neexistuje. Kompilátor prostředků nebo vizuál C++ se pokusí použít tyto soubory v adresáři určeném proměnnou prostředí **TMP** nebo aktuálním adresářem, pokud není zadaný žádný.
