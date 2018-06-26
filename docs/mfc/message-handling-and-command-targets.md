---
title: Zpracování zpráv a příkaz cíle | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- command targets [MFC]
- message handling [MFC], active documents
- IOleCommandTarget interface [MFC]
- command routing [MFC], command targets
ms.assetid: e45ce14c-e6b6-4262-8f3b-4e891e0ec2a3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: bc0f00e4f660036e73e96d4beb999d37453bdf26
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929353"
---
# <a name="message-handling-and-command-targets"></a>Zpracování zpráv a cíle příkazů
Rozhraní příkazového odesílání `IOleCommandTarget` definuje jednoduchý a rozšiřitelné mechanismus pro dotazování a spustit příkazy. Tento mechanismus je jednodušší než Automation `IDispatch` protože závisí na standardní sadu příkazů; zcela příkazy zřídka mají argumenty, a je zahrnuta žádné informace o typu (bezpečnost typů dojde ke snížení pro argumenty příkazu také).  
  
 V návrhu jednotného rozhraní dispatch příkaz každý příkaz patří "příkaz skupinu", který je sám určený s **GUID**. Proto každý, kdo můžete definovat nové skupiny a definovat všechny příkazy v rámci dané skupiny bez nutnosti ke koordinaci se společností Microsoft nebo jiného dodavatele. (Toto je v podstatě znamená stejné definice **dispinterface** plus **hodnoty dispID** ve službě Automation. Se překrývají tady, i když tento příkaz mechanismus směrování je pouze pro směrování příkazů a ne pro skriptování nebo programovatelnosti ve velkém rozsahu jako obslužné rutiny automatizace.)  
  
 `IOleCommandTarget` zpracovává následující scénáře:  
  
-   Po aktivaci, pouze se obvykle zobrazují objektu panely nástrojů a panelů nástrojů objektu může mít tlačítka pro některé příkazy kontejneru jako objekt **tiskových**, **Náhled**,  **Uložit**, **nový**, **zvětšení**a další. (Místní aktivace, které doporučujeme standardů, která objekty odebrat takové tlačítka od jejich panely nástrojů nebo v nejméně je zakázat. Tento návrh umožňuje tyto příkazy třeba povolit a ještě směruje na obslužnou rutinu správné). V současné době neexistuje žádný mechanismus pro objekt, který chcete odeslat tyto příkazy ke kontejneru.  
  
-   Pokud aktivní dokument je vložen kontejnerem aktivní dokument (jako je například modul vazby sady Office), kontejner muset odesílat příkazy takové **tiskových**, **vzhled stránky**, **vlastnosti**a další osoby mohly obsažené aktivní dokument.  
  
 Tento jednoduchý příkaz směrování může zpracovávat prostřednictvím existující automatizace standardů a `IDispatch`. Však nároky na podílejí s `IDispatch` je větší než zde, je nezbytné, `IOleCommandTarget` zajišťuje jednodušší dosáhnout skončení stejné:  
  
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
  
 `QueryStatus` Metoda zde testuje, jestli konkrétní sadu příkazů, sada se označeny **GUID**, je podporována. Toto volání vyplní celé pole **OLECMD** hodnoty (struktury) s podporovanou seznam příkazů, jakož i vrací text popisující název příkazu nebo stavové informace. Pokud má volající chce vyvolat příkaz, příkaz můžete předat (a sada **GUID**) k `Exec` společně s možností a argumenty, získávání zpět návratovou hodnotu.  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery pro aktivní dokument](../mfc/active-document-containers.md)

