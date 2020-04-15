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
ms.openlocfilehash: 98166a355fd267ecbec0a7f0cc1d18fd0b2e7cd0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353590"
---
# <a name="containers-compound-files"></a>Kontejnery: Složené soubory

Tento článek vysvětluje součásti a implementaci složených souborů a výhody a nevýhody použití složených souborů v aplikacích OLE.

Složené soubory jsou nedílnou součástí OLE. Používají se k usnadnění přenosu dat a ukládání dokumentů OLE. Složené soubory jsou implementací modelu aktivního strukturovaného úložiště. Existují konzistentní rozhraní, která podporují serializaci úložiště, datového proudu nebo objektu souboru. Složené soubory jsou podporovány v knihovně `COleStreamFile` `COleDocument`tříd Microsoft Foundation třídami a .

> [!NOTE]
> Použití složeného souboru neznamená, že informace pocházejí z dokumentu OLE nebo z složeného dokumentu. Složené soubory jsou pouze jedním ze způsobů ukládání složených dokumentů, dokumentů OLE a dalších dat.

## <a name="components-of-a-compound-file"></a><a name="_core_components_of_a_compound_file"></a>Součásti složeného souboru

Ole implementace složených souborů používá tři typy objektů: `ILockBytes` objekty datového proudu, objekty úložiště a objekty. Tyto objekty jsou podobné součástem standardního systému souborů následujícími způsoby:

- Streamujte objekty, jako jsou soubory, ukládat data libovolného typu.

- Objekty úložiště, jako jsou adresáře, mohou obsahovat další objekty úložiště a datových proudů.

- `LockBytes`objekty představují rozhraní mezi objekty úložiště a fyzickým hardwarem. Určují, jak jsou skutečné bajty zapsány `LockBytes` do libovolného paměťového zařízení, ke kterým objekt přistupuje, například na pevný disk nebo oblast globální paměti. Další informace `LockBytes` o objektech a `ILockBytes` rozhraní naleznete v odkazu *programátora OLE*.

## <a name="advantages-and-disadvantages-of-compound-files"></a><a name="_core_advantages_and_disadvantages_of_compound_files"></a>Výhody a nevýhody složených souborů

Složené soubory poskytují výhody, které nejsou k dispozici s dřívějšími metodami ukládání souborů. Patří mezi ně:

- Přírůstkový přístup k souborům.

- Režimy přístupu k souborům.

- Standardizace struktury souborů.

Při rozhodování, zda je použít ve vaší aplikaci, by měly být zváženy potenciální nevýhody složených souborů – velké velikosti a problémů s výkonem týkajících se ukládání na disketové disky.

### <a name="incremental-access-to-files"></a><a name="_core_incremental_access_to_files"></a>Přírůstkový přístup k souborům

Přírůstkový přístup k souborům je automatickou výhodou použití složených souborů. Vzhledem k tomu, že složený soubor lze zobrazit jako "systém souborů v rámci souboru", lze přistupovat k jednotlivým typům objektů, jako je datový proud nebo úložiště, aniž by bylo nutné načítat celý soubor. To může výrazně zkrátit dobu, kterou aplikace potřebuje pro přístup k novým objektům pro úpravy uživatelem. Přírůstková aktualizace založená na stejném konceptu nabízí podobné výhody. Namísto uložení celého souboru pouze pro uložení změn provedených u jednoho objektu uloží technologie OLE pouze objekt datového proudu nebo objekt úložiště upravený uživatelem.

### <a name="file-access-modes"></a><a name="_core_file_access_modes"></a>Režimy přístupu k souborům

Možnost určit, kdy jsou změny objektů ve složeném souboru potvrzeny na disk, je další výhodou použití složených souborů. Režim, ve kterém jsou k souborům přistupovány, buď transakční nebo přímé, určuje, kdy jsou změny potvrzeny.

- Transakční režim používá dvoufázovou operaci potvrzení k provedení změn objektů ve složeném souboru, čímž zachová staré i nové kopie dokumentu k dispozici, dokud se uživatel nerozhodne změny uložit nebo vrátit zpět.

- Přímý režim zahrnuje změny v dokumentu tak, jak jsou provedeny, aniž by bylo schopno je později vrátit zpět.

Další informace o režimech přístupu naleznete v *odkazu programátora OLE*.

### <a name="standardization"></a><a name="_core_standardization"></a>Normalizaci

Standardizovaná struktura složených souborů umožňuje různým aplikacím OLE procházet složené soubory vytvořené aplikací OLE bez znalosti aplikace, která soubor skutečně vytvořila.

### <a name="size-and-performance-considerations"></a><a name="_core_size_and_performance_considerations"></a>Důležité informace o velikosti a výkonu

Vzhledem ke složitosti struktury úložiště složených souborů a schopnosti ukládat data postupně, soubory používající tento formát mají tendenci být větší než jiné soubory pomocí nestrukturovaného nebo "plochého souboru" úložiště. Pokud aplikace často načítá a ukládá soubory, použití složených souborů může způsobit, že se velikost souboru zvětší mnohem rychleji než nesložené soubory. Vzhledem k tomu, že složené soubory mohou být velké, může být ovlivněna také doba přístupu k souborům uloženým a načteným z disket, což vede k pomalejšímu přístupu k souborům.

Dalším problémem, který ovlivňuje výkon je fragmentace složeného souboru. Velikost složeného souboru je určena rozdílem mezi prvním a posledním sektorem disku používaným souborem. Fragmentovaný soubor může obsahovat mnoho oblastí volného místa, které neobsahují data, ale jsou počítány při výpočtu velikosti. Během životnosti složeného souboru jsou tyto oblasti vytvořeny vložením nebo odstraněním objektů úložiště.

## <a name="using-compound-files-format-for-your-data"></a><a name="_core_using_compound_files_format_for_your_data"></a>Použití formátu složených souborů pro data

Po úspěšném vytvoření aplikace, která má `COleDocument`třídu dokumentu odvozenou od `EnableCompoundFile`, zajistěte, aby volání hlavního konstruktoru dokumentu . Když průvodce aplikací vytvoří aplikace kontejneru OLE, toto volání je vložen za vás.

V *odkazna programátor ole*, viz [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)a [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Viz také

[Containers](../mfc/containers.md)<br/>
[Kontejnery: Problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md)<br/>
[COleStreamFile – třída](../mfc/reference/colestreamfile-class.md)<br/>
[Třída COleDocument](../mfc/reference/coledocument-class.md)
