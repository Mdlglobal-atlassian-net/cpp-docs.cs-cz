---
title: COleMessageFilter Class
ms.date: 11/04/2016
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
ms.openlocfilehash: a06891f9413979895175808e109cc4abb7d75e09
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62224359"
---
# <a name="colemessagefilter-class"></a>COleMessageFilter Class

Spravují souběžnost vyžadovanou pro interakci aplikací OLE.

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
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Aplikace se vloží do zaneprázdněný stav.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Povolí nebo zakáže dialogovém okně, které se zobrazí, když volané aplikace je zaneprázdněna.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Povolí nebo zakáže dialogovém okně, které se zobrazí, když volané aplikace nereaguje.|
|[COleMessageFilter::EndBusyState](#endbusystate)|Končí zaneprázdněný stav vaší aplikace.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Volá se rozhraním zpracování zpráv, když probíhá volání OLE.|
|[COleMessageFilter::Register](#register)|Zaregistruje OLE systémové knihovny DLL filtru zpráv.|
|[COleMessageFilter::Revoke](#revoke)|Odebere registraci filtru zpráv s OLE systémové knihovny DLL.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Určuje zaneprázdněný aplikace reakce na volání rozhraní OLE.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Určuje, jak dlouho aplikace čeká na odpověď na volání rozhraní OLE.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Určuje odpověď volající aplikace zaneprázdněný aplikace.|

## <a name="remarks"></a>Poznámky

`COleMessageFilter` Třída je užitečná v visual úpravy aplikace na serveru a kontejnerů, stejně jako aplikace automatizace OLE. Pro serverové aplikace, které jsou volány Tato třída slouží k vytvoření aplikace "zaneprázdněný" tak, aby příchozí volání z jiné aplikace typu kontejner buď zrušené nebo ji zopakujete později. Tato třída slouží také k určení akce, která má být provedeny podle volající aplikace, když volané aplikace je zaneprázdněna.

Běžné použití je pro serverové aplikace volat [BeginBusyState](#beginbusystate) a [EndBusyState](#endbusystate) když bylo by nebezpečné u dokumentu nebo jiného objektu OLE přístupné zničení. Tato volání jsou provedeny v [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) během aktualizací uživatelského rozhraní.

Ve výchozím nastavení `COleMessageFilter` objektu je přiřazen, když je aplikace inicializována. Se dá načíst pomocí [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

Jedná se o pokročilé třídu; zřídka potřebujete pracovat s ním přímo.

Další informace najdete v článku [serverů: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[Třídy CObject](../../mfc/reference/cobject-class.md)

[CCmdTarget](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

##  <a name="beginbusystate"></a>  COleMessageFilter::BeginBusyState

Voláním této funkce začít zaneprázdněný stav.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Poznámky

Funguje ve spojení s [EndBusyState](#endbusystate) řídit zaneprázdněný stav vaší aplikace. Funkce [SetBusyReply](#setbusyreply) určuje odpověď aplikace zavolat aplikace, když je zaneprázdněný.

`BeginBusyState` a `EndBusyState` volání zvýší a sníží, čítač, který určuje, zda aplikace je zaneprázdněna. Například dvě volání `BeginBusyState` a volání `EndBusyState` stále výsledkem zaneprázdněný stav. Zrušit zaneprázdněný stav. je potřeba volat `EndBusyState` stejný počet, kolikrát `BeginBusyState` byla volána.

Ve výchozím nastavení, zadá rozhraní zaneprázdněný stav. během zpracování při nečinnosti, která se provádí pomocí [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Když aplikace zpracovává ON_COMMANDUPDATEUI oznámení, příchozí volání jsou zpracovány později, po dokončení zpracování při nečinnosti.

##  <a name="colemessagefilter"></a>  COleMessageFilter::COleMessageFilter

Vytvoří `COleMessageFilter` objektu.

```
COleMessageFilter();
```

##  <a name="enablebusydialog"></a>  COleMessageFilter::EnableBusyDialog

Povolí nebo zakáže dialogovém okně zaneprázdněný, který se zobrazí, když vyprší platnost zpráv čekajících zpoždění (viz [SetRetryReply](#setretryreply)) během volání OLE.

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableBusy*<br/>
Určuje, zda je povoleno "zaneprázdněný" dialogových oken.

##  <a name="enablenotrespondingdialog"></a>  COleMessageFilter::EnableNotRespondingDialog

Povolí nebo zakáže "neodpovídá" dialogovém okně, které se zobrazí v případě klávesnice nebo myši zpráva čeká na vyřízení během OLE volání a volání vypršení časového limitu.

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Parametry

*bEnableNotResponding*<br/>
Určuje, zda je povoleno dialogovém okně "neodpovídá".

##  <a name="endbusystate"></a>  COleMessageFilter::EndBusyState

Voláním této funkce na konec zaneprázdněný stav.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Poznámky

Funguje ve spojení s [BeginBusyState](#beginbusystate) řídit zaneprázdněný stav vaší aplikace. Funkce [SetBusyReply](#setbusyreply) určuje odpověď aplikace zavolat aplikace, když je zaneprázdněný.

`BeginBusyState` a `EndBusyState` volání zvýší a sníží, čítač, který určuje, zda aplikace je zaneprázdněna. Například dvě volání `BeginBusyState` a volání `EndBusyState` stále výsledkem zaneprázdněný stav. Zrušit zaneprázdněný stav. je potřeba volat `EndBusyState` stejný počet, kolikrát `BeginBusyState` byla volána.

Ve výchozím nastavení, zadá rozhraní zaneprázdněný stav. během zpracování při nečinnosti, která se provádí pomocí [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Když aplikace zpracovává ON_UPDATE_COMMAND_UI oznámení, příchozí volání jsou zpracovávány po dokončení zpracování při nečinnosti.

##  <a name="onmessagepending"></a>  COleMessageFilter::OnMessagePending

Volá se rozhraním zpracování zpráv, když probíhá volání OLE.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Ukazatel na čeká na zprávu.

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu; nenulovou hodnotu. jinak 0.

### <a name="remarks"></a>Poznámky

Při čekání na dokončení volání je volající aplikace, volá framework `OnMessagePending` s ukazatelem na čeká na zprávu. Ve výchozím nastavení rozhraní odešle zprávu WM_PAINT zprávy tak, aby aktualizace okna se můžou objevit během volání, které trvá dlouhou dobu.

Filtr zpráv je potřeba se zaregistrovat prostřednictvím volání [zaregistrovat](#register) předtím, než může být aktivní.

##  <a name="register"></a>  COleMessageFilter::Register

Zaregistruje OLE systémové knihovny DLL filtru zpráv.

```
BOOL Register();
```

### <a name="return-value"></a>Návratová hodnota

V případě úspěchu; nenulovou hodnotu. jinak 0.

### <a name="remarks"></a>Poznámky

Filtr zpráv nemá žádný vliv, pokud je zaregistrován systémové knihovny DLL. Obvykle inicializační kód vaší aplikace registruje filtr zpráv aplikace. Další filtr zpráv, registrovaných aplikace mají odvolat předtím, než program se ukončí voláním [odvolat](#revoke).

Filtr zpráv výchozí rozhraní framework je automaticky registruje se během inicializace a odvolat při ukončení.

##  <a name="revoke"></a>  COleMessageFilter::Revoke

Odvolá předchozí registraci provést voláním [zaregistrovat](#register).

```
void Revoke();
```

### <a name="remarks"></a>Poznámky

Předtím, než program se ukončí, měla by být odvolána filtru zpráv.

Výchozí filtr zpráv, který je vytvořen a zaregistrován automaticky v rámci rozhraní, je také automaticky odvolat.

##  <a name="setbusyreply"></a>  COleMessageFilter::SetBusyReply

Tato funkce nastaví aplikace "zaneprázdněný odpověď."

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Parametry

*nBusyReply*<br/>
Hodnota z `SERVERCALL` výčet, který je definován v COMPOBJ. H. Může mít některou z následujících hodnot:

- SERVERCALL_ISHANDLED aplikace může přijímat volání, ale může selhat při zpracování konkrétnímu volání.

- SERVERCALL_REJECTED aplikace pravděpodobně již nikdy nebude moct zpracovat volání.

- SERVERCALL_RETRYLATER aplikace je dočasně ve stavu, ve kterém nedokáže zpracovat volání.

### <a name="remarks"></a>Poznámky

[BeginBusyState](#beginbusystate) a [EndBusyState](#endbusystate) funkce řízení zaneprázdněný stav vaší aplikace.

Když má byla podána žádost zaneprázdněno volání `BeginBusyState`, odpoví na volání z OLE systémové knihovny DLL s hodnotou určena nastavením poslední `SetBusyReply`. Volající aplikace používá k určení jakou akci chcete provést tuto odpověď zaneprázdněn.

Ve výchozím nastavení je zaneprázdněn odpověď SERVERCALL_RETRYLATER. Tato odpověď způsobí, že volající aplikace, pokus o volání co nejdříve.

##  <a name="setmessagependingdelay"></a>  COleMessageFilter::SetMessagePendingDelay

Určuje, jak dlouho volající aplikace čeká na odpověď z názvem aplikace před přijetím další akce.

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Parametry

*nČasový limit*<br/>
Počet milisekund, zpoždění až do zprávy.

### <a name="remarks"></a>Poznámky

Tato funkce funguje společně s [SetRetryReply](#setretryreply).

##  <a name="setretryreply"></a>  COleMessageFilter::SetRetryReply

Určuje akci volající aplikace při přijetí zaneprázdněný odpověď z názvem aplikace.

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Parametry

*nRetryReply*<br/>
Počet milisekund mezi opakovanými pokusy.

### <a name="remarks"></a>Poznámky

Pokud volané aplikace znamená, že je zaneprázdněný, volající aplikace může rozhodnout počkat, až na serveru už není zaneprázdněné, opakovat okamžitě, nebo se můžete znovu po uplynutí zadaného intervalu. Také může rozhodnout zrušit volání úplně se vynechá.

Odpověď na volajícího, jež řídí funkce `SetRetryReply` a [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply` Určuje, jak dlouho má volající aplikace čekat mezi opakovanými pokusy pro daného volání. `SetMessagePendingDelay` Určuje, jak dlouho volající aplikace čeká na odpověď ze serveru než spustíte další akci.

Obvykle výchozí hodnoty jsou přijatelné a není potřeba změnit. Rozhraní framework opakování volání každých *nRetryReply* milisekund až do volání prochází nebo zpoždění zpráva čekající vypršela platnost. Hodnota 0 pro *nRetryReply* určuje okamžité opakování a - 1 určuje zrušení volání.

Pokud vypršela platnost zpráv čekajících zpoždění, OLE "zaneprázdněný dialogových oken" (Zobrazit [colebusydialog –](../../mfc/reference/colebusydialog-class.md)) se zobrazí tak, aby uživatel může zvolit zrušit nebo zopakovat volání. Volání [EnableBusyDialog](#enablebusydialog) k povolení nebo zakázání dialogovému oknu.

Když klávesnice nebo myši zpráva čeká na vyřízení během volání a volání vypršení časového limitu (překročení zpoždění čekajících zpráv), zobrazí se dialogové okno "neodpovídá". Volání [EnableNotRespondingDialog](#enablenotrespondingdialog) k povolení nebo zakázání dialogovému oknu. Tento stav obvykle označuje, že něco se pokazilo a uživatel je stále netrpělivý.

Když dialogová okna jsou zakázané, aktuální "pokus o odpověď" je vždy použít pro volání zaneprázdněný aplikacím.

## <a name="see-also"></a>Viz také:

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
