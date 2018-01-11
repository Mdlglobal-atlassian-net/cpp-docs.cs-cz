---
title: "Chyba kompilátoru prostředků RW2003 | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RW2003
dev_langs: C++
helpviewer_keywords: RW2003
ms.assetid: 9dc0ba70-6776-4aef-b316-5f1711d8e42e
caps.latest.revision: "6"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9f388ca21d95e7d675a6b9890a7368765b5c0d7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rw2003"></a>Chyba kompilátoru prostředků RW2003
Generování chyby  
  
### <a name="to-fix-by-checking-the-following-possible-causes"></a>Chcete-li vyřešit kontrolou následující možné příčiny  
  
1.  **Chyba: Soubor prostředků rastrového obrázku není ve formátu 3,00**  
  
     Rastrové obrázky v systému Windows verze 2.x formátu nelze použít ve verzi 3.x zdrojové soubory. Bitmapy musí být překreslen nebo převedeny na formát 3.x.  
  
2.  **Chyba: Staré DIB v název prostředku. Předání SDKPAINT**  
  
     Na zařízení nezávislé rastrový obrázek (DIB) v rámci zadaného prostředku není kompatibilní s formátem Windows 3.0. Bitmapy musí být překreslen nebo převedeny na formát 3.x.  
  
3.  **Chyba: Prostředků – název souboru prostředku není ve formátu 3,00**  
  
     Ikony nebo kurzoru v zadaný prostředek použít formát z předchozí verze systému Windows. Ikony nebo kurzoru musí být překreslen nebo převedeny na formát 3.x.  
  
4.  **Neznámý formát hlavičky DIB**  
  
     Hlavička rastrového obrázku není BITMAPCOREHEADER nebo BITMAPINFOHEADER strukturu.  
  
5.  **Nepodařilo se inicializovat informací o symbolu**  
  
     K této chybě dojde pouze v jazyce Visual C++. Pravděpodobná příčina je, že máte příliš mnoho souborů nebo není možné otevřít nebo zapisovat do souborů dat potřebných pro Visual C++ pro import symboly ve vašem skriptu. Visual C++ se pokusí tyto soubory vytvořit v adresáři určeného **TMP** proměnné prostředí nebo pokud není zadaný žádný aktuální adresář.  
  
6.  **Nelze uložit informací o symbolu**  
  
     K této chybě dojde pouze v jazyce Visual C++. Pravděpodobná příčina je, že máte příliš mnoho souborů nebo nelze zavřít nebo zapisovat do souborů dat potřebných pro Visual C++ pro import symboly ve vašem skriptu. Visual C++ se pokusí použít tyto soubory v adresáři určeného **TMP** proměnné prostředí nebo pokud není zadaný žádný aktuální adresář.  
  
7.  **Rastrového obrázku souboru prostředků není ve formátu 2.03**  
  
     Rastrový obrázek používá starší než verze 2.03 formátu. Bitmapy musí být převeden nebo přepracované formátu pro verzi 3,00 nebo novější.  
  
8.  **Prostředek je příliš velký**  
  
     U systému Windows 3.1 nesmí překročit prostředek přibližně 65000 bajtů. Pokud nemá prostředku, pak nebude možné kompilovat s Visual C++ nebo kompilátor příkazového řádku prostředků. Toto omezení se nevztahuje na kurzory, ikony, rastrové obrázky nebo jiným prostředkům na základě souborů.  
  
9. **Soubor prostředků není ve formátu 3,00**  
  
     Kurzor nebo ikonu používá starší než verze 3.00 formátu. Prostředek musí být převeden nebo přepracované formátu pro verzi 3,00 nebo novější.  
  
10. **Dočasný soubor nelze otevřít**  
  
     Kompilátoru/Visual C++ prostředku se nepodařilo otevřít dočasný soubor. Pravděpodobná příčina je, že nemáte oprávnění k zápisu pro adresář, nebo že adresář neexistuje. Kompilátoru/Visual C++ prostředků se pokusí použít tyto soubory v adresáři určeného **TMP** proměnné prostředí nebo pokud není zadaný žádný aktuální adresář.