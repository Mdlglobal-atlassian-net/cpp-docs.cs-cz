---
title: Chyba kompilátoru prostředků RW2003 | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2003
dev_langs:
- C++
helpviewer_keywords:
- RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9f7b4341c4567e7a58135cc99a793f287f810043
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46096779"
---
# <a name="resource-compiler-error-rw2003"></a>Chyba kompilátoru prostředků RW2003

Chyba generování

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit tak, že zkontrolujete následující možné příčiny

1. **Chyba: Soubor prostředků – rastrového obrázku není ve formátu 3.00**

     Rastrové obrázky ve formátu Windows verze 2.x nelze použít v souborech prostředků verze 3.x. Rastrový obrázek musí být překreslení nebo převedeny na formát 3.x.

1. **Chyba: Staré DIB v názvu prostředku. Prochází SDKPAINT**

     Na zařízení nezávislé rastrového obrázku (DIB) v zadaný prostředek není kompatibilní s formátem Windows 3.0. Rastrový obrázek musí být překreslení nebo převedeny na formát 3.x.

1. **Chyba: Prostředek název souboru prostředku není ve formátu 3.00**

     Ikony nebo kurzoru v zadaného prostředku používaný formát z předchozí verze systému Windows. Ikony nebo kurzoru musí být překreslení nebo převedeny na formát 3.x.

1. **Neznámý formát DIB záhlaví**

     Hlavička rastrového obrázku není BITMAPCOREHEADER nebo BITMAPINFOHEADER strukturu.

1. **Nepovedlo se inicializovat informace o symbolech**

     K této chybě dochází pouze v jazyce Visual C++. Nejpravděpodobnější příčinou je, že máte moc otevřených souborů nebo nelze otevřít nebo zápis do datových souborů potřebných pro Visual C++ pro import symboly ve vašem skriptu. Visual C++ se pokusí vytvořit tyto soubory v adresáři určeném argumentem **TMP** proměnné prostředí nebo aktuálního adresáře, pokud není zadaný žádný.

1. **Nepovedlo se uložit informace o symbolech**

     K této chybě dochází pouze v jazyce Visual C++. Nejpravděpodobnější příčinou je, že máte moc otevřených souborů nebo nelze zavřít nebo zápis do datových souborů potřebných pro Visual C++ pro import symboly ve vašem skriptu. Visual C++ se pokouší použít tyto soubory v adresáři určeném argumentem **TMP** proměnné prostředí nebo aktuálního adresáře, pokud není zadaný žádný.

1. **Soubor prostředků soubor rastrového obrázku není ve formátu 2.03**

     Rastrový obrázek používá formát starší než verze 2.03 nástroje MkTypLib.exe. Rastrový obrázek musí být převedená nebo přepracované ve formátu verze 3.00 nebo novější.

1. **Prostředek je příliš velký**

     Windows 3.1 prostředek nesmí přesáhnout přibližně 65000 bajtů. Pokud je váš prostředek, pak nebudete mít pro kompilaci pomocí jazyka Visual C++ nebo nástroje příkazového řádku resource compiler. Toto omezení se nevztahuje na kurzory, ikony, bitmapy nebo další souborové prostředky.

9. **Soubor prostředků není ve formátu 3.00**

     Kurzor nebo ikona používá starší než verze 3.00 formátu. Prostředek musí být převedená nebo přepracované ve formátu verze 3.00 nebo novější.

10. **Nepodařilo se otevřít dočasný soubor**

     Kompilátor/Visual C++ prostředků se nepodařilo otevřít dočasný soubor. Nejpravděpodobnější příčinou je, že nemáte oprávnění k zápisu pro adresář nebo že adresář neexistuje. Prostředek kompilátoru/Visual C++ se pokouší použít tyto soubory v adresáři určeném argumentem **TMP** proměnné prostředí nebo aktuálního adresáře, pokud není zadaný žádný.