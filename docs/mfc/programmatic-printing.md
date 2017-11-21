---
title: "Tisk prostřednictvím kódu programu | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- printing [MFC], active documents
- active documents [MFC], printing
- printing [MFC], programmatic
- IPrint interface
- printing [MFC]
ms.assetid: 3db0945b-5e13-4be4-86a0-6aecdae565bd
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 037e32f5284ab27c072f09c8965009eca1d0e7c7
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="programmatic-printing"></a>Tisk prostřednictvím kódu programu
OLE poskytuje prostředky k jednoznačné identifikaci trvalé dokumentů (**GetClassFile**) a načíst je do jejich přidružených kódu (`CoCreateInstance`, **QueryInterface(IID_IPersistFile)**, **QueryInterface(IID_IPersistStorage)**, **IPersistFile::Load**, a **IPersistStorage::Load**). Další povolit tisk dokumentů, obsahování pro aktivní dokument (pomocí existujícímu návrhu OLE není součástí OLE 2.0 původně) představuje základ standardní tisk rozhraní, `IPrint`, obecně k dispozici prostřednictvím jakéhokoliv objektu, který může načíst trvalý stav typu dokumentu. Každé zobrazení aktivní dokument může volitelně podporovat **IPrint –** rozhraní k poskytování těchto funkcí.  
  
 `IPrint` Rozhraní je definován následujícím způsobem:  
  
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
  
 Klienty a kontejnery jednoduše používat **IPrint::Print** dáte pokyn, aby dokument Tisk samotné po tento dokument je načtena, zadání tisku příznaky ovládacích prvků, cílové zařízení, na stránkách tisknout a další možnosti. Klienta můžete také ovládat pokračování tisk přes rozhraní `IContinueCallback` (viz níže).  
  
 Kromě toho **IPrint::SetInitialPageNum** podporuje možnost tisknout řadu dokumenty, jak ji číslování stránky bezproblémově, samozřejmě výhody pro kontejnery pro aktivní dokument jako vazby sady Office. **IPrint::GetPageInfo** díky zobrazení informací o stránkování jednoduché tím, že volající načíst počáteční stránka číslo dříve předaný **SetInitialPageNum** (nebo interní výchozí dokumentu Počáteční číslo stránky) a počet stránek v dokumentu.  
  
 Objektů, které podporují `IPrint` jsou v registru označené jako "Printable" klíč uložený v objektu CLSID:  
  
 HKEY_CLASSES_ROOT\CLSID\\{...} \Printable  
  
 `IPrint`Obvykle se implementuje na stejný objekt, který podporuje buď `IPersistFile` nebo `IPersistStorage`. Volající Poznámka: schopnost trvalý stav některé třídy tak, že vyhledá v registru pro klíč "Printable" Tisk prostřednictvím kódu programu. V současné době "Tisknutelná" udává podporu alespoň `IPrint`; dalších rozhraní může být definována v budoucnu který pak bude k dispozici prostřednictvím `QueryInterface` kde **IPrint –** jednoduše představuje základní úroveň podpory.  
  
 Během tisku postup můžete klienta nebo kontejner, který spustil tisk řídit, jestli by měly pokračovat tisku. Kontejner může například podporovat příkaz "Zastavit vytisknout", který by měl co nejdříve ukončit tiskové úlohy. Na podporu této možnosti, můžete klienta tisknutelná objektu implementovat podřízený objekt malé oznámení s rozhraním `IContinueCallback`:  
  
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
  
 Toto rozhraní umožňuje sloužit jako obecný pokračování funkci zpětného volání, která probíhá různé postupy pokračování v rozhraní API Win32 (například **AbortProc** pro tisk a  **EnumMetafileProc** pro výčet metafile). Proto tento návrh rozhraní je užitečné v celé řadě časově náročné procesů.  
  
 V případech nejvíce Obecné **IContinueCallback::FContinue** funkce pravidelně volá všechny zdlouhavý proces. Vrátí podřízený objekt `S_OK` budete v operaci pokračovat a **S_FALSE** zastavení procesu co nejdříve.  
  
 **FContinue**, ale není použit v rámci **IPrint::Print**; místo toho tisk používá **IContinueCallback::FContinuePrint**. Jakýkoli tisk objekt by měly volat pravidelně **FContinuePrinting** předávání na počet stránek, které mají tisk přes, číslo stránky, tisku a další řetězec popisující stav tisku, který může klient Vyberte zobrazení pro uživatele (například "stránka 5 19").  
  
## <a name="see-also"></a>Viz také  
 [Kontejnery pro aktivní dokument](../mfc/active-document-containers.md)

