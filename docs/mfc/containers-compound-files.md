---
title: 'Kontejnery: Složené soubory'
ms.date: 11/04/2016
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
ms.openlocfilehash: 5a8ba0821d92ab41a4b95fb7b2a26da63c1df285
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643262"
---
# <a name="containers-compound-files"></a>Kontejnery: Složené soubory

Tento článek vysvětluje, komponenty a implementaci složených souborů a výhody a nevýhody použití složené soubory ve vašich aplikacích OLE.

Složené soubory jsou nedílnou součástí OLE. Používají se pro usnadnění přenos dat a úložiště dokumentu OLE. Složené soubory jsou implementace modelu aktivního strukturované úložiště. Konzistentní rozhraní existovat tuto podporu serializace za účelem úložiště, datového proudu nebo souboru objektu. Složené soubory jsou podporovány v knihovny Microsoft Foundation Class v rámci tříd `COleStreamFile` a `COleDocument`.

> [!NOTE]
>  Pomocí složeného souboru neznamená, že informace pocházejí z dokumentu OLE nebo složeném dokumentu. Složené soubory se jenom jeden ze způsobů, jak ukládat složených dokumentů, OLE – dokumenty a další data.

##  <a name="_core_components_of_a_compound_file"></a> Součástí složeného souboru

OLE – implementace složené soubory používá tři typy objektů: objektů datového proudu, objekty úložiště a `ILockBytes` objekty. Tyto objekty jsou podobné součásti standardní systém souborů následujícími způsoby:

- Stream objekty, jako jsou soubory, ukládání dat libovolného typu.

- Objekty úložiště, jako je adresáře, mohou obsahovat další objekty úložiště a datový proud.

- `LockBytes` objekty představují rozhraní mezi objekty úložiště a na fyzickém hardwaru. Určují, jak skutečný počet bajtů se zapisují do libovolné zařízení úložiště `LockBytes` přístup k objektu, například pevný disk nebo oblasti globální paměti. Další informace o `LockBytes` objekty a `ILockBytes` rozhraní, najdete v článku *OLE referenční informace pro programátory*.

##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a> Výhody a nevýhody složené soubory

Složené soubory poskytuje výhody není k dispozici u předchozích metod služby file storage. Mezi ně patří:

- Přístup k přírůstkové souboru.

- Soubor režimy přístupu.

- Standardizace struktura souborů.

Potenciální nevýhodou složené soubory – velký velikostní a výkonové problémy týkající se úložiště na diskety – by měly být považovány za při rozhodování o tom, jestli se má použít v aplikaci.

###  <a name="_core_incremental_access_to_files"></a> Přírůstkové přístup k souborům

Přírůstkové přístup k souborům je automatické výhodou použití složené soubory. Protože zobrazením složeném souboru jako "systému souborů v rámci souboru" přístupný jednotlivého objektu typy, jako je datový proud nebo úložiště, aniž by bylo nutné načíst celý soubor. To výrazně zkrátit čas, aplikace potřebuje pro přístup k nové objekty pro úpravy uživatelem. Přírůstkové aktualizace založené na stejný koncept podobné výhody nabídky. Místo uložení celého souboru jenom na Uložit změny provedené na jeden objekt OLE uloží pouze datový proud nebo úložiště objekt upraven uživatelem.

###  <a name="_core_file_access_modes"></a> Režimy přístupu k souboru

Další výhodou používání složené soubory nebudou moct zjistit, když změny objektů ve složeném souboru usilujeme o to na disk je. Režim, ve kterém k souborům, počet nebo přímým přístupem, určuje, kdy se změny potvrdí.

- Počet zrušených zpracovaných režimu používá dvoufázového potvrzení operaci provést změny na objekty ve složeném souboru, a tím zachovat původní a nové kopie dokument k dispozici, dokud uživatel zvolí možnost uložit nebo vrátit zpět změny.

- Přímý režim zahrnuje změny v dokumentu, jako byly provedeny, kdybychom neměli možnost později vrátit zpět.

Další informace o režimech přístup, najdete v článku *OLE referenční informace pro programátory*.

###  <a name="_core_standardization"></a> Standardizace

Standardizované struktura složené soubory umožňuje různé aplikace OLE procházet složené soubory vytvořené ve vašich aplikacích OLE bez znalosti aplikace, která se automaticky vytvoří soubor.

###  <a name="_core_size_and_performance_considerations"></a> Velikost a důležité informace o výkonu

Z důvodu složitosti struktury složený soubor úložiště a možnost uložení dat přírůstkově pomocí tohoto formátu souborů mají tendenci větší než ostatní soubory pomocí nestrukturovaných nebo "plochého souboru" úložiště. Pokud vaše aplikace často načte a uloží soubory, pomocí složených souborů může způsobit velikost souboru ke zvýšení mnohem rychleji než noncompound soubory. Protože složené soubory mohou být velké, čas přístupu pro soubory uložené na a načíst z disketové jednotky můžete také mít vliv, výsledkem je pomalejší přístup k souborům.

Jiný problém, který má vliv na výkon je fragmentaci složeného souboru. Velikost složeného souboru je určeno rozdílu mezi prvním a posledním disku sektory, které soubor používá. Fragmentovaný soubor může obsahovat mnoho oblasti volného místa, které neobsahují data, ale se počítají při výpočtu velikosti. Po celou dobu životnosti složený soubor vytvářejí tyto oblasti vložení nebo odstranění objektů úložiště.

##  <a name="_core_using_compound_files_format_for_your_data"></a> Složené soubory formátu vašich dat

Po úspěšném vytvoření aplikace, která má dokument třídy odvozené od `COleDocument`, ujistěte se, že váš hlavní dokument Konstruktor volá `EnableCompoundFile`. Pokud Průvodce aplikace vytvoří aplikace typu kontejner OLE, vloží se pro vás toto volání.

V *OLE referenční informace pro programátory*, naleznete v tématu [IStream](/windows/desktop/api/objidl/nn-objidl-istream), [IStorage](/windows/desktop/api/objidl/nn-objidl-istorage), a [ILockBytes](/windows/desktop/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Viz také

[Kontejnery](../mfc/containers.md)<br/>
[Kontejnery: Problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md)<br/>
[COleStreamFile – třída](../mfc/reference/colestreamfile-class.md)<br/>
[COleDocument – třída](../mfc/reference/coledocument-class.md)
