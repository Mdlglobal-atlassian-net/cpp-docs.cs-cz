---
title: Zpracování zpráv a cíle příkazů
ms.date: 11/04/2016
f1_keywords:
- IOleCommandTarget
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
ms.openlocfilehash: f9212e32605a1fed179c931d4f63833e17870b5c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50442533"
---
# <a name="message-handling-and-command-targets"></a>Zpracování zpráv a cíle příkazů

Rozhraní odbavení příkaz `IOleCommandTarget` definuje jednoduchý a rozšiřitelný mechanismus pro dotazování a příkazy. Tento mechanismus je jednodušší než služby Automation `IDispatch` protože spoléhá výhradně na standardní sadu příkazů; příkazy zřídka mít argumenty a nepodílí žádné informace o typu (bezpečnost typů je oslabená a argumentů příkazu).

V návrhu rozhraní odeslání příkazu, každý příkaz patří "příkaz skupina", který je sám určený pomocí **GUID**. Proto všem uživatelům můžete definovat nové skupiny a definovat všechny příkazy v dané skupině bez nutnosti ke koordinaci se společností Microsoft nebo jiného dodavatele. (To je v podstatě stejným způsobem jako definice **dispinterface** plus **dispID** ve službě Automation. Se překrývají, i když tento příkaz směrování mechanismus je pouze pro směrování příkazů a ne pro skriptování a programování ve velkém měřítku jako obslužné rutiny služby Automation.)

`IOleCommandTarget` zpracovává následující scénáře:

- Po aktivaci, pouze panely nástrojů objektu se obvykle zobrazují a panelů nástrojů objekt může mít tlačítek u některých příkazů kontejneru, jako je objekt **tisk**, **Náhled**,  **Uložit**, **nový**, **přiblížení**a další. (Aktivace na místě, které doporučujeme standardy, které objekty odebrat tyto tlačítka z jejich panely nástrojů, nebo na nejméně je zakázat. Toto řešení umožňuje tyto příkazy povoleny a ještě směrovat na obslužnou rutinu správné). V současné době neexistuje způsob, object odesláním těchto příkazů do kontejneru.

- Při vložení aktivního dokumentu v aktivním dokumentu kontejneru (například modul vazby sady Office) kontejneru možná bude nutné posílat příkazy takové **tisk**, **vzhled stránky**, **vlastnosti**a další obsažené aktivní dokument.

Tento jednoduchý příkaz směrování může zpracovat přes existující automatizace standardy a `IDispatch`. Ale nároky na péči o `IDispatch` je vyšší, než je nutný zde, takže `IOleCommandTarget` nabízí jednodušší způsob k dosažení stejného elementy end:

```
interface IOleCommandTarget : IUnknown
    {
    HRESULT QueryStatus(
        [in] GUID *pguidCmdGroup,
        [in] ULONG cCmds,
        [in,out][size_is(cCmds)] OLECMD *prgCmds,
        [in,out] OLECMDTEXT *pCmdText);
    HRESULT Exec(
        [in] GUID *pguidCmdGroup,
        [in] DWORD nCmdID,
        [in] DWORD nCmdExecOpt,
        [in] VARIANTARG *pvaIn,
        [in,out] VARIANTARG *pvaOut);
    }
```

`QueryStatus` Metoda zde testuje, jestli konkrétní sadu příkazů, sady jsou označené pomocí **GUID**, se podporuje. Toto volání vyplní celou řadu **OLECMD** hodnoty (struktury) seznam podporovaných příkazů, jakož i vrací text popisující název příkazu nebo stavové informace. Při spuštění příkazu si přeje volajícího, lze předat příkazu (a sada **GUID**) k `Exec` spolu s možností a argumentů, návrat návratovou hodnotu.

## <a name="see-also"></a>Viz také

[Kontejnery pro aktivní dokument](../mfc/active-document-containers.md)

