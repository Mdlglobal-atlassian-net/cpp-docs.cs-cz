---
title: Tisk prostřednictvím kódu programu
ms.date: 11/04/2016
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
ms.openlocfilehash: d01dcd901425fb3957201dca754a01042e629ebb
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50630656"
---
# <a name="programmatic-printing"></a>Tisk prostřednictvím kódu programu

Poskytuje prostředky k jednoznačné identifikaci trvalé dokumenty OLE (`GetClassFile`) a načíst je do jejich přidružený kód (`CoCreateInstance`, `QueryInterface(IID_IPersistFile)`, `QueryInterface(IID_IPersistStorage)`, `IPersistFile::Load`, a `IPersistStorage::Load`). Další povolit tisk dokumentů, zahrnutí aktivního dokumentu (pomocí existující návrh OLE nejsou dodávané současně s OLE 2.0 původně) představuje základ standard tisk rozhraní, `IPrint`, všeobecně dostupná prostřednictvím libovolného objektu, který lze načíst trvalý stav typu dokumentu. Každé zobrazení aktivního dokumentu může volitelně podporovat `IPrint` rozhraní k poskytování těchto funkcí.

`IPrint` Rozhraní je definovaná následujícím způsobem:

```
interface IPrint : IUnknown
    {
    HRESULT SetInitialPageNum([in] LONG nFirstPage);
    HRESULT GetPageInfo(
        [out] LONG *pnFirstPage,
        [out] LONG *pcPages);
    HRESULT Print(
        [in] DWORD grfFlags,
        [in,out] DVTARGETDEVICE **pptd,
        [in,out] PAGESET ** ppPageSet,
        [in,out] STGMEDIUM **ppstgmOptions,
        [in] IContinueCallback* pCallback,
        [in] LONG nFirstPage,
        [out] LONG *pcPagesPrinted,
        [out] LONG *pnPageLast);
    };
```

Klienti a kontejnerů jednoduše použít `IPrint::Print` dáte pokyn, aby dokument, aby se vytiskl po načtení dokumentu zadání tisk příznaky ovládacích prvků, cílové zařízení, stránky, které vytisknout a další možnosti. Klienta můžete také řídit pokračování tisk přes rozhraní `IContinueCallback` (viz níže).

Kromě toho `IPrint::SetInitialPageNum` podporuje schopnost vytisknou řadu dokumenty, jak ho číslování stránky bez problémů, samozřejmě výhoda pro kontejnery pro aktivní dokument jako modul vazby sady Office. `IPrint::GetPageInfo` Umožňuje zobrazit informace o stránkování jednoduché tím, že volající načíst počáteční stránky číslo dřív Bezproblémová `SetInitialPageNum` (nebo dokumentu interní výchozí počáteční číslo stránky) a počet stránek v dokumentu.

Objekty, které podporují `IPrint` jsou označeny "Printable" klíč uložený v objektu CLSID v registru:

HKEY_CLASSES_ROOT\CLSID\\{...} \Printable

`IPrint` Obvykle se implementuje na stejný objekt, který podporuje buď `IPersistFile` nebo `IPersistStorage`. Volající mějte na paměti umožňuje trvalý stav některé třídy vyhledáváním v registru pro klíč "Printable" Tisk prostřednictvím kódu programu. V současné době "Tisknutelný" označuje podporu pro alespoň `IPrint`; jiná rozhraní lze definovat v budoucnu které pak budou k dispozici prostřednictvím `QueryInterface` kde `IPrint` jednoduše představuje základní úroveň podpory.

Během tiskové postup můžete klienta nebo kontejner, který inicioval tisk řídit, jestli by měl tisku pokračovat. Kontejner může například podporovat příkaz "Stop Print", který by měla ukončit tisková úloha co nejdříve. Na podporu této možnosti, můžete klienta tisknutelný objekt implementovat objekt jímka malé oznámení pomocí rozhraní `IContinueCallback`:

```
interface IContinueCallback : IUnknown
    {
    HRESULT FContinue(void);
    HRESULT FContinuePrinting(
        [in] LONG cPagesPrinted,
        [in] LONG nCurrentPage,
        [in] LPOLESTR pszPrintStatus);
    };
```

Toto rozhraní je navržena jako užitečné jako funkce zpětného volání obecných pokračování, které u něho různých postupů pokračování v rozhraní API systému Win32 (třeba `AbortProc` pro tisk a `EnumMetafileProc` pro výčet metafile). Proto tento návrh rozhraní je užitečné v celé řadě časově náročné procesy.

V nejvíce obecný případech `IContinueCallback::FContinue` funkce pravidelně volá všechny časově náročný proces. Objekt jímky vrátí S_OK operace tak bude pokračovat a S_FALSE zastavit proces co nejdříve.

`FContinue`, ale není použit v rámci `IPrint::Print`; místo toho používá tisk `IContinueCallback::FContinuePrint`. Libovolný objekt pro tisk pravidelně by měly volat `FContinuePrinting` předávání počet stránek, které mají tisk přes, číslo stránky, tisku a další řetězec popisující stav tisku na klienta můžete zobrazit uživateli (například "stránka 5 19").

## <a name="see-also"></a>Viz také

[Kontejnery pro aktivní dokument](../mfc/active-document-containers.md)

