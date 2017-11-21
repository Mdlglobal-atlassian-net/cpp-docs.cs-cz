---
title: "Kontejnery: Složené soubory | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- compound files [MFC]
- compound documents
- containers [MFC], compound files
- OLE documents [MFC], compound files
- performance [MFC], compound files
- files [MFC], compound
- standardized file structure compound files
- documents [MFC], compound
- documents [MFC], OLE
- OLE containers [MFC], compound files
- access modes for files [MFC]
ms.assetid: 8b83cb3e-76c8-4bbe-ba16-737092b36f49
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e48915641abae2285f00dcc24328efd810ec5e68
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="containers-compound-files"></a>Kontejnery: Složené soubory
Tento článek vysvětluje součásti a provádění složené soubory a výhody a nevýhody použití složené soubory ve svých aplikacích OLE.  
  
 Složené soubory jsou nedílnou součástí OLE. Používají se pro usnadnění přenos dat a ukládání dokumentů OLE. Složené soubory jsou implementace Active strukturovaného úložiště modelu. Konzistentní rozhraní existovat tuto podporu serializace úložiště, datový proud nebo objekt souboru. Složené soubory jsou podporovány ve knihovny Microsoft Foundation Class pomocí třídy `COleStreamFile` a `COleDocument`.  
  
> [!NOTE]
>  Pomocí složeného souboru neznamená, jestli informace pocházejí z dokument OLE nebo složeného dokumentu. Složené soubory jsou jen jedním ze způsobů k uložení složených dokumentů, OLE – dokumenty a další data.  
  
##  <a name="_core_components_of_a_compound_file"></a>Komponenty složené souboru  
 Implementace OLE složené soubory používá tři typy objektů: objektů datového proudu, objektů úložiště a `ILockBytes` objekty. Tyto objekty jsou podobné součástí standardní systém souborů následujícími způsoby:  
  
-   Datový proud objekty, jako jsou soubory, ukládání dat jakéhokoli typu.  
  
-   Úložiště objekty, jako jsou adresáře, může obsahovat jiné objekty úložiště a datového proudu.  
  
-   **LockBytes** objekty představují rozhraní mezi objekty úložiště a fyzický hardware. Určují, jak se zapisují aktuální počet bajtů na jakémkoli zařízení úložiště **LockBytes** přístup k objektu, například pevný disk nebo oblast globální paměti. Další informace o **LockBytes** objekty a `ILockBytes` rozhraní najdete v tématu *OLE referenční informace pro programátory*.  
  
##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a>Výhody a nevýhody složené soubory  
 Složené soubory poskytnout starší metody úložiště file výhody není k dispozici. Mezi ně patří:  
  
-   Přístup k přírůstkové souboru.  
  
-   Soubor režimy přístupu.  
  
-   Standardizace strukturu souborů.  
  
 Potenciální nevýhody složené soubory – velká velikost a výkon problémy týkající se úložiště na diskety – by měl být považovány při rozhodování, zda je použít v aplikaci.  
  
###  <a name="_core_incremental_access_to_files"></a>Přírůstkové přístup k souborům  
 Přírůstkové přístup k souborům je automatické výhodou používání složené soubory. Protože složený soubor lze zobrazit jako "systém souborů v souboru", je možné přistupovat typy jednotlivých objektů, jako je datový proud nebo úložiště, aniž by bylo nutné načíst celý soubor. Tato akce může výrazně snížit čas aplikace potřebuje přístup k nové objekty pro úpravy uživatelem. Přírůstkové aktualizace, založené na stejný koncept, podobné výhody nabídky. Místo uložení celý soubor právě se uložit změny provedené v jeden objekt, uloží OLE pouze datový proud nebo úložiště objektu uživatel upravit.  
  
###  <a name="_core_file_access_modes"></a>Režimy přístupu k souboru  
 Další výhodou používání složené soubory schopnost určit, kdy jsou změny provedené u objektů v souboru složené zapsat na disk je. Režim, ve kterém k souborům, zpracovaných nebo přímé, určuje, kdy jsou změny potvrzeny.  
  
-   Zpracované režimu používá operaci na dvoufázový zápis objektů v složený soubor, a tím zachování starý i nové kopie dokumentu, které jsou k dispozici, dokud uživatel vybere možnost uložení nebo vrátit zpět změny provést změny.  
  
-   Přímý režim zahrnuje změny v dokumentu, protože byly provedeny, aniž by je mohli později vrátit zpět.  
  
 Další informace o režimech přístupu najdete v tématu *OLE referenční informace pro programátory*.  
  
###  <a name="_core_standardization"></a>Standardizace  
 Standardizovaná strukturu složené soubory umožňuje jiné aplikace rozhraní OLE procházet složené soubory vytvořené v aplikaci OLE bez znalosti aplikace, která ve skutečnosti vytvořil soubor.  
  
###  <a name="_core_size_and_performance_considerations"></a>Velikost a důležité informace o výkonu  
 Z důvodu složitosti strukturu úložiště složený soubor a možnosti k uložení dat postupně, soubory formátu mají tendenci musí být větší než ostatní soubory pomocí nestrukturovaných nebo "plochém souboru" úložiště. Pokud vaše aplikace často načítá a ukládá soubory, může způsobit pomocí složené soubory mnohem rychleji než soubory noncompound zvýšit velikost souboru. Protože složené soubory mohou být velký, čas přístupu pro soubory uložené na a načíst z disketové jednotky může mít vliv i, výsledkem je pomalejší přístup k souborům.  
  
 Jinému problému, který má vliv na výkon je fragmentace složené souboru. Velikost složené souboru je určen podle rozdíl mezi první a poslední diskových sektorech, kterou soubor používá. Fragmentovaný soubor může obsahovat mnoho oblasti volného místa, které neobsahují data, ale při výpočtu velikosti, se počítají. Po dobu platnosti složený soubor tyto oblasti jsou vytvořené vložení nebo odstranění objektů úložiště.  
  
##  <a name="_core_using_compound_files_format_for_your_data"></a>Složené soubory formátu pro Data  
 Po úspěšném vytvoření aplikace, která má dokumentu třídy odvozené od `COleDocument`, ujistěte se, že volá konstruktor vaší hlavní dokumentu `EnableCompoundFile`. Když v Průvodce vytvořením aplikace vytvoří OLE – aplikace typu kontejner, vloží se toto volání za vás.  
  
 V *OLE referenční informace pro programátory*, najdete v části [IStream on Request](http://msdn.microsoft.com/library/windows/desktop/aa380034), [IStorage](http://msdn.microsoft.com/library/windows/desktop/aa380015), a [ILockBytes](http://msdn.microsoft.com/library/windows/desktop/aa379238).  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery](../mfc/containers.md)   
 [Kontejnery: Problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md)   
 [COleStreamFile – třída](../mfc/reference/colestreamfile-class.md)   
 [COleDocument – třída](../mfc/reference/coledocument-class.md)
