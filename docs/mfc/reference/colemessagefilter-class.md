---
title: "Třída COleMessageFilter | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- COleMessageFilter
- AFXOLE/COleMessageFilter
- AFXOLE/COleMessageFilter::COleMessageFilter
- AFXOLE/COleMessageFilter::BeginBusyState
- AFXOLE/COleMessageFilter::EnableBusyDialog
- AFXOLE/COleMessageFilter::EnableNotRespondingDialog
- AFXOLE/COleMessageFilter::EndBusyState
- AFXOLE/COleMessageFilter::OnMessagePending
- AFXOLE/COleMessageFilter::Register
- AFXOLE/COleMessageFilter::Revoke
- AFXOLE/COleMessageFilter::SetBusyReply
- AFXOLE/COleMessageFilter::SetMessagePendingDelay
- AFXOLE/COleMessageFilter::SetRetryReply
dev_langs: C++
helpviewer_keywords:
- COleMessageFilter [MFC], COleMessageFilter
- COleMessageFilter [MFC], BeginBusyState
- COleMessageFilter [MFC], EnableBusyDialog
- COleMessageFilter [MFC], EnableNotRespondingDialog
- COleMessageFilter [MFC], EndBusyState
- COleMessageFilter [MFC], OnMessagePending
- COleMessageFilter [MFC], Register
- COleMessageFilter [MFC], Revoke
- COleMessageFilter [MFC], SetBusyReply
- COleMessageFilter [MFC], SetMessagePendingDelay
- COleMessageFilter [MFC], SetRetryReply
ms.assetid: b1fd1639-fac4-4fd0-bf17-15172deba13c
caps.latest.revision: "21"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 8c8ad9086520a7a9f12869cf35e3a11a10673659
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="colemessagefilter-class"></a>COleMessageFilter – třída
Spravuje souběžnosti vyžaduje interakci aplikace rozhraní OLE.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class COleMessageFilter : public CCmdTarget  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Vytvoří `COleMessageFilter` objektu.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Vloží zaneprázdněn stavu aplikace.|  
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Povolí nebo zakáže okno, které se zobrazí, když názvem aplikace je zaneprázdněná.|  
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Povolí nebo zakáže okno, které se zobrazí, když neodpovídá názvem aplikace.|  
|[COleMessageFilter::EndBusyState](#endbusystate)|Ukončí zaneprázdněn stavu aplikace.|  
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Voláno rámcem zpracování zpráv, když probíhá volání OLE.|  
|[COleMessageFilter::Register](#register)|Registruje filtr zpráv OLE systémové knihovny DLL.|  
|[COleMessageFilter::Revoke](#revoke)|Odvolá filtr zpráv registrace OLE systémové knihovny DLL.|  
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Určuje zaneprázdněn aplikace odpovědi na volání rozhraní OLE.|  
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Určuje, jak dlouho aplikace čeká na odpověď na volání rozhraní OLE.|  
|[COleMessageFilter::SetRetryReply](#setretryreply)|Určuje odpověď je volající aplikace k zaneprázdněn aplikaci.|  
  
## <a name="remarks"></a>Poznámky  
 `COleMessageFilter` Třída je užitečná v visual serveru a kontejneru aplikace pro úpravy, jakož i aplikace automatizace OLE. Pro serverové aplikace, které se označují jako tato třída slouží k zpřístupnění aplikace "zaneprázdněn" tak, aby zrušené příchozí volání z jiné aplikace typu kontejner nebo jejich opakovat později. Tato třída slouží také k určení akce, které mají být provedeny volání aplikace při vyvolání aplikace je zaneprázdněná.  
  
 Běžné použití je pro serverové aplikace volání [BeginBusyState](#beginbusystate) a [EndBusyState](#endbusystate) při by být nebezpečný pro dokument nebo jiné dostupné objekt OLE zničení. V těchto volání [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) během aktualizace uživatelského rozhraní.  
  
 Ve výchozím nastavení `COleMessageFilter` objektu je přiřazen při inicializaci aplikace. Se dá načíst pomocí [afxolegetmessagefilter –](application-control.md#afxolegetmessagefilter).  
  
 Toto je pokročilé třídy; potřebujete málokdy s ním pracovat přímo.  
  
 Další informace najdete v článku [servery: implementace serveru](../../mfc/servers-implementing-a-server.md).  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CCmdTarget](../../mfc/reference/ccmdtarget-class.md)  
  
 `COleMessageFilter`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** afxole.h  
  
##  <a name="beginbusystate"></a>COleMessageFilter::BeginBusyState  
 Volání této funkce zahájíte zaneprázdněn stavu.  
  
```  
virtual void BeginBusyState();
```  
  
### <a name="remarks"></a>Poznámky  
 Funguje ve spojení s [EndBusyState](#endbusystate) k řízení zaneprázdněn stavu aplikace. Funkce [SetBusyReply](#setbusyreply) určuje odpověď aplikace k volání aplikace, pokud je zaneprázdněný.  
  
 `BeginBusyState` a `EndBusyState` volání zvýší a sníží, čítač, který určuje, zda je zaneprázdněn. Například dvě volání `BeginBusyState` a jedno volání `EndBusyState` stále výsledek v zaneprázdněn stavu. Zrušit zaneprázdněn stavu, je nutné volat `EndBusyState` stejný počet `BeginBusyState` byla volána.  
  
 Ve výchozím nastavení, zadá rozhraní zaneprázdněn stavu během zpracování při nečinnosti, která se provádí pomocí [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Když aplikace zpracovává **ON_COMMANDUPDATEUI** oznámení, příchozí volání zpracovává později, po dokončení zpracování při nečinnosti.  
  
##  <a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter  
 Vytvoří `COleMessageFilter` objektu.  
  
```  
COleMessageFilter();
```  
  
##  <a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog  
 Povolí nebo zakáže zaneprázdněn dialogu, který se zobrazí, když vyprší platnost zpoždění čeká na zprávu (viz [SetRetryReply](#setretryreply)) v průběhu hovoru OLE.  
  
```  
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnableBusy*  
 Určuje, zda je povoleno dialogové okno "zaneprázdněn".  
  
##  <a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog  
 Povolí nebo zakáže "neodpovídá" dialogu, který se zobrazí, pokud se čeká na zprávu klávesnici nebo myš během OLE volání a volání vypršení časového limitu.  
  
```  
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```  
  
### <a name="parameters"></a>Parametry  
 *bEnableNotResponding*  
 Určuje, zda je povoleno dialogové okno "neodpovídá".  
  
##  <a name="endbusystate"></a>COleMessageFilter::EndBusyState  
 Volání této funkce na konec zaneprázdněn stavu.  
  
```  
virtual void EndBusyState();
```  
  
### <a name="remarks"></a>Poznámky  
 Funguje ve spojení s [BeginBusyState](#beginbusystate) k řízení zaneprázdněn stavu aplikace. Funkce [SetBusyReply](#setbusyreply) určuje odpověď aplikace k volání aplikace, pokud je zaneprázdněný.  
  
 `BeginBusyState` a `EndBusyState` volání zvýší a sníží, čítač, který určuje, zda je zaneprázdněn. Například dvě volání `BeginBusyState` a jedno volání `EndBusyState` stále výsledek v zaneprázdněn stavu. Zrušit zaneprázdněn stavu, je nutné volat `EndBusyState` stejný počet `BeginBusyState` byla volána.  
  
 Ve výchozím nastavení, zadá rozhraní zaneprázdněn stavu během zpracování při nečinnosti, která se provádí pomocí [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Když aplikace zpracovává `ON_UPDATE_COMMAND_UI` oznámení, příchozí volání zpracovává po dokončení zpracování při nečinnosti.  
  
##  <a name="onmessagepending"></a>COleMessageFilter::OnMessagePending  
 Voláno rámcem zpracování zpráv, když probíhá volání OLE.  
  
```  
virtual BOOL OnMessagePending(const MSG* pMsg);
```  
  
### <a name="parameters"></a>Parametry  
 `pMsg`  
 Ukazatel na čeká na zprávu.  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Při čekání na dokončení volání je volající aplikace, volá framework `OnMessagePending` pomocí ukazatele na čeká na zprávu. Ve výchozím nastavení, odešle zprávu rozhraní `WM_PAINT` zpráv, tak, aby okno aktualizace může dojít během volání, která trvá dlouhou dobu.  
  
 Je nutné zaregistrovat vaše filtr zpráv prostřednictvím volání [zaregistrovat](#register) může stát aktivní.  
  
##  <a name="register"></a>COleMessageFilter::Register  
 Registruje filtr zpráv OLE systémové knihovny DLL.  
  
```  
BOOL Register();
```  
  
### <a name="return-value"></a>Návratová hodnota  
 Nenulové hodnoty v případě úspěchu; jinak 0.  
  
### <a name="remarks"></a>Poznámky  
 Filtr zpráv nemá žádný vliv, pokud není zaregistrována systémové knihovny DLL. Inicializace kódu vaší aplikace obvykle zaregistruje filtr zpráv aplikace. Další filtr zpráv, zaregistrovaný vaše aplikace by měla odvolávat před program ukončí voláním [odvolat](#revoke).  
  
 Rozhraní framework výchozí zprávu filtr je automaticky zaregistrován během inicializace a odvolat na ukončení.  
  
##  <a name="revoke"></a>COleMessageFilter::Revoke  
 Odvolá předchozí registrace provádí volání [zaregistrovat](#register).  
  
```  
void Revoke();
```  
  
### <a name="remarks"></a>Poznámky  
 Filtr zpráv zbaven před program ukončí.  
  
 Výchozí filtr zpráv, které se vytvoří a zaregistruje se automaticky rámcem, je také automaticky odvolat.  
  
##  <a name="setbusyreply"></a>COleMessageFilter::SetBusyReply  
 Tato funkce nastaví aplikace "zaneprázdněn odpovědi."  
  
```  
void SetBusyReply(SERVERCALL nBusyReply);
```  
  
### <a name="parameters"></a>Parametry  
 *nBusyReply*  
 Hodnota z `SERVERCALL` výčtu, která je definována v COMPOBJ. H. Může mít jednu z následujících hodnot:  
  
- **SERVERCALL_ISHANDLED** aplikace může přijímat volání, ale při zpracování volání konkrétní se nemusí zdařit.  
  
- **SERVERCALL_REJECTED** nikdy pravděpodobně aplikace budou moci zpracování hovoru.  
  
- **SERVERCALL_RETRYLATER** aplikace je dočasně ve stavu, ve kterém it nelze zpracovat volání.  
  
### <a name="remarks"></a>Poznámky  
 [BeginBusyState](#beginbusystate) a [EndBusyState](#endbusystate) funkce řízení zaneprázdněn stavu aplikace.  
  
 Když aplikace byl proveden zaneprázdněn prováděním volání `BeginBusyState`, odpoví na volání z knihovny DLL systému OLE s hodnotou určený nastavením poslední `SetBusyReply`. Volající aplikace používá k určení jakou akci chcete provést tuto zaneprázdněn odpověď.  
  
 Ve výchozím nastavení, je zaneprázdněn odpovědi **SERVERCALL_RETRYLATER**. Tato odpověď způsobí, že je volající aplikace k volání co nejdříve opakovat.  
  
##  <a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay  
 Určuje, jak dlouho je volající aplikace čeká na odpověď od názvem aplikace před provedením další akce.  
  
```  
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```  
  
### <a name="parameters"></a>Parametry  
 `nTimeout`  
 Počet milisekund pro zpoždění čeká na zprávu.  
  
### <a name="remarks"></a>Poznámky  
 Tato funkce funguje v souladu s [SetRetryReply](#setretryreply).  
  
##  <a name="setretryreply"></a>COleMessageFilter::SetRetryReply  
 Určuje akci volající aplikace při obdržení zaneprázdněn odpovědi z názvem aplikace.  
  
```  
void SetRetryReply(DWORD nRetryReply = 0);
```  
  
### <a name="parameters"></a>Parametry  
 `nRetryReply`  
 Počet milisekund mezi opakovanými pokusy.  
  
### <a name="remarks"></a>Poznámky  
 Při vyvolání aplikace označuje, že je zaneprázdněný, počkejte, dokud server je zaneprázdněný, zkuste ji nezaznamenáte okamžitě, nebo po určité době opakujte už může rozhodnout volající aplikace. Může také rozhodnout zcela zrušit volání.  
  
 Odpověď volajícího se řídí funkce `SetRetryReply` a [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply`Určuje, jak dlouho má volající aplikace čekat mezi opakovanými pokusy pro danou volání. `SetMessagePendingDelay`Určuje, jak dlouho je volající aplikace čeká na odpověď od serveru před provedením další akce.  
  
 Obvykle výchozí hodnoty jsou přijatelné a není potřeba změnit. Rozhraní framework opakování volání každých `nRetryReply` milisekundách dokud prochází volání nebo zpoždění čeká na zprávu vypršela. Hodnota 0 pro `nRetryReply` určuje okamžitou opakování a - 1 znamená zrušení volání.  
  
 Pokud vypršela platnost zpoždění čeká na zprávu, OLE "zaneprázdněn dialogových oken" (viz [COleBusyDialog](../../mfc/reference/colebusydialog-class.md)), zobrazí se uživateli můžete vybrat možnost zrušení nebo volání opakovat. Volání [EnableBusyDialog](#enablebusydialog) k povolení nebo zakázání tohoto dialogového okna.  
  
 Když klávesnici nebo myš zpráva čeká na vyřízení během volání a volání časový limit (překročena zpoždění čeká na zprávu), se zobrazí dialogové okno "neodpovídá". Volání [EnableNotRespondingDialog](#enablenotrespondingdialog) k povolení nebo zakázání tohoto dialogového okna. Tento stav obvykle označuje, že něco nepovede a uživatel je získávání netrpělivý.  
  
 Když jsou zakázané v dialogových oknech, aktuální "opakování odpověď" vždy slouží pro volání zaneprázdněn aplikací.  
  
## <a name="see-also"></a>Viz také  
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)   
 [Graf hierarchie](../../mfc/hierarchy-chart.md)   
 [CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
