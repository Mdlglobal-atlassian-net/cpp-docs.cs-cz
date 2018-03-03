---
title: "TN071: MFC IOleCommandTarget – implementace | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- IOleCommandTarget
dev_langs:
- C++
helpviewer_keywords:
- TN071 [MFC]
- IOleCommandTarget interface [MFC]
ms.assetid: 3eef571e-6357-444d-adbb-6f734a0c3161
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 43f97774036c42fa0f681a65e0a335f944daf09c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="tn071-mfc-iolecommandtarget-implementation"></a>TN071: MFC IOleCommandTarget – implementace
> [!NOTE]
>  Následující Technická poznámka nebyla aktualizována vzhledem k tomu, že byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata může být zastaralý nebo není správný. Nejnovější informace se doporučuje, vyhledejte téma týkající se v indexu online dokumentaci.  
  
 `IOleCommandTarget` Rozhraní umožňuje objekty a jejich kontejnery odesílání příkazů k sobě navzájem. Například objektu panely nástrojů může obsahovat tlačítka pro příkazy, jako například **tiskových**, **Náhled**, **Uložit**, `New`, a **přiblížení**. Pokud byly v kontejneru, který podporuje vložených takového objektu `IOleCommandTarget`, může povolit jeho tlačítka a předávat příkazy ke kontejneru pro zpracování při kliknutí na uživatele, je objekt. Pokud kontejner chtěli vložený objekt tisknout sám sebe, vytvoření této žádosti odesláním příkazu prostřednictvím `IOleCommandTarget` rozhraní vložený objekt.  
  
 `IOleCommandTarget`Automatizace jako rozhraní je v tom, že klient je používána k vyvolání metody na serveru. Však pomocí `IOleCommandTarget` uloží režii volání prostřednictvím rozhraní automatizace protože programátory nemusíte používat obvykle levnější `Invoke` metodu `IDispatch`.  
  
 V prostředí MFC `IOleCommandTarget` rozhraní používá servery pro aktivní dokument k povolení kontejnery pro aktivní dokument k odesílání příkazů na server. Třída serveru aktivní dokument, `CDocObjectServerItem`, používá mapy rozhraní MFC (najdete v části [TN038: MFC/OLE – implementace třídy IUnknown](../mfc/tn038-mfc-ole-iunknown-implementation.md)) k implementaci `IOleCommandTarget` rozhraní.  
  
 `IOleCommandTarget`také je implementována ve **COleFrameHook** třídy. **COleFrameHook** nedokumentovanými třídy MFC, která implementuje funkce okno rámečkem na místě upravuje kontejnery. **COleFrameHook** také používá mapy MFC rozhraní k implementaci `IOleCommandTarget` rozhraní. **COleFrameHook**na implementaci `IOleCommandTarget` předává OLE příkazů `COleDocObjectItem`-odvozené kontejnery pro aktivní dokument. To umožňuje žádné kontejner služby MFC Active dokumentu pro příjem zpráv ze serverů obsažené aktivní dokument.  
  
## <a name="mfc-ole-command-maps"></a>Mapy příkazů OLE MFC  
 MFC vývojáři mohou využít výhod `IOleCommandTarget` pomocí MFC OLE příkaz mapy. Mapy příkazů OLE jsou jako mapy zpráv, protože je možné použít k mapování příkazy OLE na členské funkce třídy, která obsahuje příkaz mapy. Chcete-li tato práce, umístěte makra v mapě příkaz zadat příkaz OLE skupiny chcete zpracovat příkaz, příkaz OLE a ID příkazu [wm_command –](http://msdn.microsoft.com/library/windows/desktop/ms647591) zprávu, která bude odeslána, když je obdržena příkaz OLE. MFC také poskytuje řadu předdefinovaných makra pro standardní příkazy OLE. Seznam standardní OLE příkazy, které byly původně navrženy pro pomocí aplikace Microsoft Office naleznete v tématu OLECMDID výčtu, která je definována v docobj.h.  
  
 Pokud byl přijat příkaz OLE MFC aplikací, která obsahuje mapování příkaz OLE MFC se pokusí najít ID příkazu a skupina příkazu pro požadovaný příkaz v mapě příkaz OLE aplikace. Pokud je nalezena shoda, **wm_command –** zpráva odeslána na aplikace obsahující příkaz mapy s ID požadovaný příkaz. (Viz popis `ON_OLECMD` níže.) Tímto způsobem jsou příkazy OLE odeslat do aplikace převedena na **wm_command –** zprávy v prostředí MFC. **Wm_command –** zprávy jsou poté směrován přes mapy zpráv aplikace přes standardní MFC [směrování příkazů](../mfc/command-routing.md) architektura.  
  
 Na rozdíl od mapy zpráv mapy příkazů MFC OLE nepodporuje ClassWizard. Vývojáři MFC musí ručně přidat podporu mapy příkazů OLE a položek mapování příkaz OLE. OLE mapy příkazů mohou být přidány do knihovny MFC aktivní dokument servery do třídy, která je v **wm_command –** řetězu směrování zprávy v době aktivní dokument je aktivní na místě v kontejneru. Tyto třídy zahrnují třídy odvozené od třídy aplikace [CWinApp](../mfc/reference/cwinapp-class.md), [CView](../mfc/reference/cview-class.md), [CDocument](../mfc/reference/cdocument-class.md), a [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md). V kontejnery pro aktivní dokument, mapy příkazů OLE lze přidat pouze k [COleDocObjectItem](../mfc/reference/coledocobjectitem-class.md)-odvozené třídy. Také v kontejnery pro aktivní dokument **wm_command –** zprávy bude odeslána pouze k mapy zpráv v `COleDocObjectItem`-odvozené třídy.  
  
## <a name="ole-command-map-macros"></a>Makra Map příkaz OLE  
 Pomocí následující makra přidejte příkaz mapy funkce do vaší třídy:  
  
```  
 
DECLARE_OLECMD_MAP ()  
 
```  
  
 Toto makro přejde v deklaracích třídy (obvykle ve hlavičkový soubor) třídy, která obsahuje příkaz mapy.  
  
```  
 
BEGIN_OLECMD_MAP(
theClass  ,   baseClass)  
 
```  
  
 `theClass`  
 Název třídy, která obsahuje příkaz mapy.  
  
 `baseClass`  
 Název třídy základní třídy, která obsahuje příkaz mapy.  
  
 Toto makro označuje začátek příkaz mapy. Použití tohoto makra v souboru implementace pro třídu, která obsahuje příkaz mapy.  
  
```  
 
END_OLECMD_MAP()  
 
```  
  
 Toto makro označuje konec příkazu mapy. Použití tohoto makra v souboru implementace pro třídu, která obsahuje příkaz mapy. Toto makro nutné provést **BEGIN_OLECMD_MAP** makro.  
  
```  
 
ON_OLECMD(
pguid  ,   
olecmdid  ,
    id)  
 
```  
  
 `pguid`  
 Ukazatel na identifikátor GUID skupina příkazu příkaz OLE. Tento parametr je **NULL** pro standardní skupinu příkaz OLE.  
  
 *olecmdid*  
 ID příkazu OLE příkazu, který má být volána.  
  
 `id`  
 ID **wm_command –** zpráva k odeslání do aplikace obsahující příkaz mapy, při vyvolání tento příkaz OLE.  
  
 Použití `ON_OLECMD` makro v mapě příkaz pro přidání položek pro OLE příkazy, které chcete zpracovávat. Když příkazy OLE přijme, bude převeden do zadané **wm_command –** zpráva a směrován přes mapy zpráv aplikace pomocí architektury standardní směrování příkazů MFC.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat schopnost OLE zpracování příkazu je MFC aktivní server dokumentu pro zpracování [OLECMDID_PRINT](http://msdn.microsoft.com/library/windows/desktop/ms691264) příkaz OLE. Tento příklad předpokládá, že jste použili k vygenerování MFC aplikace, která je aktivní dokument server objekty AppWizard.  
  
1.  V vaše `CView`-odvozené třídy záhlaví souboru, přidejte `DECLARE_OLECMD_MAP` makro k deklaraci třídy.  
  
    > [!NOTE]
    >  Použití `CView`-odvozené třídy, protože se jedná o jednu z tříd na serveru pro aktivní dokument, který je v **wm_command –** směrování zpráv řetězu.  
  
 ```  
    class CMyServerView : public CView  
 {  
    protected: // create from serialization only  
    CMyServerView();
DECLARE_DYNCREATE(CMyServerView)  
    DECLARE_OLECMD_MAP() 
 . . .  
 };  
 ```  
  
2.  V souboru implementace `CView`-odvozené třídy, přidejte `BEGIN_OLECMD_MAP` a `END_OLECMD_MAP` makra:  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView, CView)  
 
    END_OLECMD_MAP() 
 ```  
  
3.  Pro zpracování příkazu print standardní OLE, přidejte [on_olecmd –](reference/message-map-macros-mfc.md#on_olecmd) makro mapování příkazu zadání OLE ID příkazu pro příkaz standardní tiskové a **id_file_print –** pro **wm_command –**  ID. **Id_file_print –** je standard ID tiskové příkazu, který používá aplikace generované objekty AppWizard MFC:  
  
 ```  
    BEGIN_OLECMD_MAP(CMyServerView,
    CView)  
    ON_OLECMD(NULL,
    OLECMDID_PRINT,
    ID_FILE_PRINT) 
    END_OLECMD_MAP() 
 ```  
  
 Upozorňujeme, že jednu standardní příkaz maker OLE definovaných v afxdocob.h, může být místě `ON_OLECMD` makro protože **OLECMDID_PRINT** je standardní OLE ID příkazu. `ON_OLECMD_PRINT` Makro bude možné provést stejný úkol, jako `ON_OLECMD` makro uvedené výše.  
  
 Když aplikace kontejneru odešle tento server **OLECMDID_PRINT** příkaz prostřednictvím serveru `IOleCommandTarget` rozhraní MFC tisk obslužná rutina příkazu, který bude vyvolán na serveru, způsobit server tisknout aplikace. Kontejner pro aktivní dokument kód k vyvolání příkazu print přidat v předchozích krocích by vypadat přibližně takto:  
  
```  
void CContainerCntrItem::DoOleCmd()  
{  
    IOleCommandTarget *pCmd = NULL;  
    HRESULT hr = E_FAIL;  
    OLECMD ocm={OLECMDID_PRINT, 0};  
 
    hr = m_lpObject->QueryInterface(IID_IOleCommandTarget,reinterpret_cast<void**>(&pCmd));

    if(FAILED(hr)) 
    return; 
 
    hr = pCmd->QueryStatus(NULL, 1, &ocm, NULL);

    if(SUCCEEDED(hr)&& (ocm.cmdf& OLECMDF_ENABLED))  
 { *//Command is available and enabled so call it  
    COleVariant vIn;  
    COleVariant vOut;  
    hr = pCmd->Exec(NULL, OLECMDID_PRINT,  
    OLECMDEXECOPT_DODEFAULT, &vIn, &vOut);

    ASSERT(SUCCEEDED(hr));

 }  
    pCmd->Release();

} 
```  
  
## <a name="see-also"></a>Viz také  
 [Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)   
 [Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)

