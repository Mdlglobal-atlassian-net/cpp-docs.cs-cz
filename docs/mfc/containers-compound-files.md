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
ms.openlocfilehash: cc34f5ed32ee48d538b67cab080b0a52b2e00ae8
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69508886"
---
# <a name="containers-compound-files"></a>Kontejnery: Složené soubory

Tento článek vysvětluje komponenty a implementaci složených souborů a výhody a nevýhody použití složených souborů v aplikacích OLE.

Složené soubory jsou nedílnou součástí OLE. Slouží k usnadnění přenosu dat a ukládání dokumentů OLE. Složené soubory jsou implementací aktivního modelu strukturovaného úložiště. Existují konzistentní rozhraní, které podporuje serializaci do úložiště, datového proudu nebo objektu souboru. Složené soubory jsou podporovány v Knihovna Microsoft Foundation Class třídami `COleStreamFile` a. `COleDocument`

> [!NOTE]
>  Použití složeného souboru neznamená, že informace pocházejí z dokumentu OLE nebo složeného dokumentu. Složené soubory jsou pouze jedním ze způsobů ukládání složených dokumentů, dokumentů OLE a dalších dat.

##  <a name="_core_components_of_a_compound_file"></a>Komponenty složeného souboru

Implementace složeného souboru OLE používá tři typy objektů: streamování objektů, objektů úložiště a `ILockBytes` objektů. Tyto objekty jsou podobné komponentám standardního systému souborů následujícími způsoby:

- Streamování objektů, jako jsou soubory, ukládat data libovolného typu.

- Objekty úložiště, jako jsou adresáře, můžou obsahovat další objekty úložiště a streamování.

- `LockBytes`objekty reprezentují rozhraní mezi objekty úložiště a fyzickým hardwarem. Určují, jak se zapisují skutečné bajty do libovolného úložného zařízení `LockBytes` , ke kterému objekt přistupuje, jako je například pevný disk nebo oblast globální paměti. Další informace o `LockBytes` objektech `ILockBytes` a rozhraní naleznete v tématu *reference programátora OLE*.

##  <a name="_core_advantages_and_disadvantages_of_compound_files"></a>Výhody a nevýhody složených souborů

Složené soubory poskytují výhody, které nejsou k dispozici v dřívějších metodách úložiště souborů. Mezi ně patří:

- Přírůstkový přístup k souborům

- Režimy přístupu k souboru.

- Standardizace struktury souborů

Potenciální nevýhody složených souborů – problémy s velkým objemem a výkonem, které se týkají úložiště na disketách, by měly být zváženy při rozhodování, zda je chcete ve své aplikaci použít.

###  <a name="_core_incremental_access_to_files"></a>Přírůstkový přístup k souborům

Přírůstkový přístup k souborům je automatická výhoda použití složených souborů. Vzhledem k tomu, že složený soubor lze zobrazit jako "systém souborů v rámci souboru", je možné použít jednotlivé typy objektů, například datový proud nebo úložiště, bez nutnosti načíst celý soubor. To může výrazně zkrátit dobu, po kterou aplikace potřebuje přístup k novým objektům pro úpravy uživatelem. Přírůstková aktualizace založená na stejném konceptu nabízí podobné výhody. Místo uložení celého souboru jenom pro uložení změn provedených u jednoho objektu uloží OLE jenom datový proud nebo objekt úložiště upravovaný uživatelem.

###  <a name="_core_file_access_modes"></a>Režimy přístupu k souborům

Schopnost určit, kdy jsou změny objektů ve složeném souboru potvrzeny na disk, je další výhodou použití složených souborů. Režim, ve kterém jsou soubory k dispozici, buď v transakčním, nebo přímo, určují, kdy jsou změny potvrzeny.

- V transakčním režimu se používá dvoufázové operace potvrzení, která provádí změny objektů ve složeném souboru, a udržuje tak staré i nové kopie dokumentu k dispozici, dokud se uživatel nerozhodne buď změny uložit, nebo zrušit.

- Přímý režim zahrnuje změny v dokumentu, protože jsou provedeny, aniž by bylo možné je později vrátit zpět.

Další informace o režimech přístupu naleznete v *referenci programátora OLE*.

###  <a name="_core_standardization"></a>Standardizace

Standardizovaná struktura složených souborů umožňuje různým aplikacím OLE procházet složené soubory vytvořené aplikací OLE bez znalosti aplikace, která soubor skutečně vytvořila.

###  <a name="_core_size_and_performance_considerations"></a>Požadavky na velikost a výkon

Z důvodu složitosti struktury složeného úložiště souborů a možnosti ukládat data přírůstkově jsou soubory v tomto formátu obvykle větší než jiné soubory pomocí úložiště nestrukturovaných nebo plochých souborů. Pokud vaše aplikace často načítá a ukládá soubory, může použití složených souborů způsobit zvětšení velikosti souboru mnohem rychleji než nesložené soubory. Vzhledem k tomu, že složené soubory můžou být velké, může to mít vliv na přístup k souborům uloženým na disketě a zavedených z disket, což má za následek pomalejší přístup k souborům.

Dalším problémem, který má vliv na výkon, je fragmentace složeného souboru. Velikost složeného souboru je určena rozdílem mezi prvním a posledním diskovým sektorem používaným souborem. Fragmentované soubory mohou obsahovat mnoho oblastí volného místa, které neobsahují data, ale budou počítány při výpočtu velikosti. Během životnosti složeného souboru jsou tyto oblasti vytvářeny vložením nebo odstraněním objektů úložiště.

##  <a name="_core_using_compound_files_format_for_your_data"></a>Použití formátu složených souborů pro vaše data

Po úspěšném vytvoření aplikace, která má třídu dokumentu odvozenou `COleDocument`od, se ujistěte, že váš konstruktor `EnableCompoundFile`hlavního dokumentu volá. Když průvodce aplikací vytvoří aplikace OLE kontejneru, toto volání je vloženo za vás.

V *referenci programátora OLE*, viz [IStream](/windows/win32/api/objidl/nn-objidl-istream), [IStorage](/windows/win32/api/objidl/nn-objidl-istorage)a [ILockBytes](/windows/win32/api/objidl/nn-objidl-ilockbytes).

## <a name="see-also"></a>Viz také:

[Kontejnery](../mfc/containers.md)<br/>
[Kontejnery: Problémy uživatelského rozhraní](../mfc/containers-user-interface-issues.md)<br/>
[COleStreamFile – třída](../mfc/reference/colestreamfile-class.md)<br/>
[COleDocument – třída](../mfc/reference/coledocument-class.md)
