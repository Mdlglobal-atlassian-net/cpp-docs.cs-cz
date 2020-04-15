---
title: Třída COleMessageFilter
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
ms.openlocfilehash: f6db5f012aedf08edd87980e304e181295bfb953
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374916"
---
# <a name="colemessagefilter-class"></a>Třída COleMessageFilter

Spravuje souběžnost vyžadožnou interakcí aplikací OLE.

## <a name="syntax"></a>Syntaxe

```
class COleMessageFilter : public CCmdTarget
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[COleMessageFilter::COleMessageFilter](#colemessagefilter)|Vytvoří `COleMessageFilter` objekt.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[COleMessageFilter::BeginBusyState](#beginbusystate)|Umístí aplikaci do stavu zaneprázdněn.|
|[COleMessageFilter::EnableBusyDialog](#enablebusydialog)|Povolí a zakáže dialogové okno, které se zobrazí, když je volaná aplikace zaneprázdněna.|
|[COleMessageFilter::EnableNotRespondingDialog](#enablenotrespondingdialog)|Povolí a zakáže dialogové okno, které se zobrazí, když volaná aplikace neodpovídá.|
|[COleMessageFilter::EndBusyState](#endbusystate)|Ukončí zaneprázdněný stav aplikace.|
|[COleMessageFilter::OnMessagePending](#onmessagepending)|Volat rámci ke zpracování zpráv, zatímco probíhá volání OLE.|
|[COleMessageFilter::Registrovat](#register)|Zaregistruje filtr zpráv pomocí knihoven DLL systému OLE.|
|[COleMessageFilter::Odvolat](#revoke)|Odvolá registraci filtru zpráv u knihoven DLL systému OLE.|
|[COleMessageFilter::SetBusyReply](#setbusyreply)|Určuje odpověď zaneprázdněné aplikace na volání OLE.|
|[COleMessageFilter::SetMessagePendingDelay](#setmessagependingdelay)|Určuje, jak dlouho aplikace čeká na odpověď na volání OLE.|
|[COleMessageFilter::SetRetryReply](#setretryreply)|Určuje odpověď volající aplikace na zaneprázdněnou aplikaci.|

## <a name="remarks"></a>Poznámky

Třída `COleMessageFilter` je užitečná v aplikacích vizuálních úprav serveru a kontejnerů, stejně jako v aplikacích automatizace OLE. Pro serverové aplikace, které jsou volány, lze tuto třídu použít k tomu, aby byla aplikace "zaneprázdněna", takže příchozí volání z jiných aplikací kontejneru jsou zrušena nebo opakována později. Tuto třídu lze také použít k určení akce, která má být provedena volající aplikací, když je volaná aplikace zaneprázdněna.

Běžné použití je pro serverové aplikace volat [BeginBusyState](#beginbusystate) a [EndBusyState,](#endbusystate) pokud by bylo nebezpečné pro dokument nebo jiný objekt přístupný ole, které mají být zničeny. Tato volání jsou prováděny v [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle) během aktualizace uživatelského rozhraní.

Ve výchozím `COleMessageFilter` nastavení je objekt přidělen při inicializování aplikace. Lze načíst pomocí [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

Toto je pokročilá třída; málokdy s ním potřebujete pracovat přímo.

Další informace naleznete v článku [Servery: Implementace serveru](../../mfc/servers-implementing-a-server.md).

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

[CObjekt](../../mfc/reference/cobject-class.md)

[CCmdCíl](../../mfc/reference/ccmdtarget-class.md)

`COleMessageFilter`

## <a name="requirements"></a>Požadavky

**Záhlaví:** afxole.h

## <a name="colemessagefilterbeginbusystate"></a><a name="beginbusystate"></a>COleMessageFilter::BeginBusyState

Volání této funkce zahájit zaneprázdněný stav.

```
virtual void BeginBusyState();
```

### <a name="remarks"></a>Poznámky

Pracuje ve spojení s [EndBusyState](#endbusystate) řídit stavu zaneprázdněn aplikace. Funkce [SetBusyReply](#setbusyreply) určuje odpověď aplikace na volání aplikací, když je zaneprázdněna.

A `BeginBusyState` `EndBusyState` volání přírůstek a snížení, respektive čítač, který určuje, zda je aplikace zaneprázdněna. Například dvě volání `BeginBusyState` a jedno `EndBusyState` volání stále za následek zaneprázdněný stav. Chcete-li zrušit zaneprázdněný stav, je nutné volat `EndBusyState` stejný počet, kolikrát `BeginBusyState` byl volán.

Ve výchozím nastavení rozhraní přejde do stavu zaneprázdněn během zpracování nečinnosti, který je prováděn [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Zatímco aplikace zpracovává ON_COMMANDUPDATEUI oznámení, příchozí volání jsou zpracovány později, po dokončení nečinnosti zpracování.

## <a name="colemessagefiltercolemessagefilter"></a><a name="colemessagefilter"></a>COleMessageFilter::COleMessageFilter

Vytvoří `COleMessageFilter` objekt.

```
COleMessageFilter();
```

## <a name="colemessagefilterenablebusydialog"></a><a name="enablebusydialog"></a>COleMessageFilter::EnableBusyDialog

Povolí a zakáže zaneprázdněné dialogové okno, které se zobrazí po vypršení zpoždění čekající na zprávu (viz [SetRetryReply)](#setretryreply)během volání OLE.

```
void EnableBusyDialog(BOOL bEnableBusy = TRUE);
```

### <a name="parameters"></a>Parametry

*povolitZaneprázdněn*<br/>
Určuje, zda je dialogové okno Zaneprázdněn povoleno nebo zakázáno.

## <a name="colemessagefilterenablenotrespondingdialog"></a><a name="enablenotrespondingdialog"></a>COleMessageFilter::EnableNotRespondingDialog

Povolí a zakáže dialogové okno "neodpovídá", které se zobrazí, pokud během volání OLE čeká na vyřízení zprávy klávesnice nebo myši a časový čas volání bylo zakázáno.

```
void EnableNotRespondingDialog(BOOL bEnableNotResponding = TRUE);
```

### <a name="parameters"></a>Parametry

*benableNotResponding*<br/>
Určuje, zda je dialogové okno "neodpovídá" povoleno nebo zakázáno.

## <a name="colemessagefilterendbusystate"></a><a name="endbusystate"></a>COleMessageFilter::EndBusyState

Volání této funkce ukončit zaneprázdněný stav.

```
virtual void EndBusyState();
```

### <a name="remarks"></a>Poznámky

Pracuje ve spojení s [BeginBusyState](#beginbusystate) řídit zaneprázdněný stav aplikace. Funkce [SetBusyReply](#setbusyreply) určuje odpověď aplikace na volání aplikací, když je zaneprázdněna.

A `BeginBusyState` `EndBusyState` volání přírůstek a snížení, respektive čítač, který určuje, zda je aplikace zaneprázdněna. Například dvě volání `BeginBusyState` a jedno `EndBusyState` volání stále za následek zaneprázdněný stav. Chcete-li zrušit zaneprázdněný stav, je nutné volat `EndBusyState` stejný počet, kolikrát `BeginBusyState` byl volán.

Ve výchozím nastavení rozhraní přejde do stavu zaneprázdněn během zpracování nečinnosti, který je prováděn [CWinApp::OnIdle](../../mfc/reference/cwinapp-class.md#onidle). Zatímco aplikace zpracovává ON_UPDATE_COMMAND_UI oznámení, příchozí volání jsou zpracovány po dokončení nečinnosti zpracování.

## <a name="colemessagefilteronmessagepending"></a><a name="onmessagepending"></a>COleMessageFilter::OnMessagePending

Volat rámci ke zpracování zpráv, zatímco probíhá volání OLE.

```
virtual BOOL OnMessagePending(const MSG* pMsg);
```

### <a name="parameters"></a>Parametry

*pMsg*<br/>
Ukazatel na čekající zprávu.

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="remarks"></a>Poznámky

Pokud volající aplikace čeká na dokončení volání, rozhraní `OnMessagePending` framework volá s ukazatelem čekající zprávy. Ve výchozím nastavení rozhraní framework odešle WM_PAINT zprávy, takže aktualizace okna může dojít během volání, které trvá dlouhou dobu.

Filtr zpráv je nutné zaregistrovat pomocí volání [register,](#register) než se může stát aktivním.

## <a name="colemessagefilterregister"></a><a name="register"></a>COleMessageFilter::Registrovat

Zaregistruje filtr zpráv pomocí knihoven DLL systému OLE.

```
BOOL Register();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová na úspěch; jinak 0.

### <a name="remarks"></a>Poznámky

Filtr zpráv nemá žádný vliv, pokud není registrován u systémových knihoven DLL. Kód inicializace aplikace obvykle registruje filtr zpráv aplikace. Jakýkoli jiný filtr zpráv registrovaný vaší aplikací by měl být odvolán před ukončením programu voláním [revoke](#revoke).

Výchozí filtr zpráv rozhraní je automaticky zaregistrován během inicializace a odvolán při ukončení.

## <a name="colemessagefilterrevoke"></a><a name="revoke"></a>COleMessageFilter::Odvolat

Odvolá předchozí registraci provedenou voláním [do rejstříku](#register).

```
void Revoke();
```

### <a name="remarks"></a>Poznámky

Filtr zpráv by měl být před ukončením programu odvolán.

Výchozí filtr zpráv, který je vytvořen a automaticky registrován v rámci, je také automaticky odvolán.

## <a name="colemessagefiltersetbusyreply"></a><a name="setbusyreply"></a>COleMessageFilter::SetBusyReply

Tato funkce nastaví "zaneprázdněnou odpověď" aplikace.

```
void SetBusyReply(SERVERCALL nBusyReply);
```

### <a name="parameters"></a>Parametry

*nZaneprázdněná odpověď*<br/>
Hodnota z `SERVERCALL` výčtu, která je definována v compobj. H. Může mít některou z následujících hodnot:

- SERVERCALL_ISHANDLED Aplikace může přijímat volání, ale může selhat při zpracování konkrétního volání.

- SERVERCALL_REJECTED Aplikace pravděpodobně nikdy nebude moci zpracovat volání.

- SERVERCALL_RETRYLATER Aplikace je dočasně ve stavu, ve kterém nemůže zpracovat volání.

### <a name="remarks"></a>Poznámky

Funkce [BeginBusyState](#beginbusystate) a [EndBusyState](#endbusystate) řídí stav zaneprázdnění aplikace.

Pokud byla aplikace zaneprázdněna voláním `BeginBusyState`, reaguje na volání ze systému OLE knihovny DLL `SetBusyReply`s hodnotou určenou posledním nastavením aplikace . Volající aplikace používá tuto zaneprázdněnou odpověď k určení, jakou akci provést.

Ve výchozím nastavení je zaneprázdněná odpověď SERVERCALL_RETRYLATER. Tato odpověď způsobí, že volající aplikace zopakovat volání co nejdříve.

## <a name="colemessagefiltersetmessagependingdelay"></a><a name="setmessagependingdelay"></a>COleMessageFilter::SetMessagePendingDelay

Určuje, jak dlouho volající aplikace čeká na odpověď z volané aplikace před provedením další akce.

```
void SetMessagePendingDelay(DWORD nTimeout = 5000);
```

### <a name="parameters"></a>Parametry

*nČasový režim*<br/>
Počet milisekund pro zpoždění čekající na zprávu.

### <a name="remarks"></a>Poznámky

Tato funkce funguje ve shodě s [SetRetryReply](#setretryreply).

## <a name="colemessagefiltersetretryreply"></a><a name="setretryreply"></a>COleMessageFilter::SetRetryReply

Určuje akci volající aplikace, když obdrží zaneprázdněnou odpověď z volané aplikace.

```
void SetRetryReply(DWORD nRetryReply = 0);
```

### <a name="parameters"></a>Parametry

*nRetryReply*<br/>
Počet milisekund mezi opakovanými pokusy.

### <a name="remarks"></a>Poznámky

Pokud volaná aplikace označuje, že je zaneprázdněna, může se volající aplikace rozhodnout počkat, dokud server není zaneprázdněn, a to ihned zopakovat nebo opakovat po zadaném intervalu. Může se také rozhodnout hovor zcela zrušit.

Odpověď volajícího je řízena `SetRetryReply` funkcemi a [SetMessagePendingDelay](#setmessagependingdelay). `SetRetryReply`určuje, jak dlouho by volající aplikace měla čekat mezi opakovanými pokusy pro dané volání. `SetMessagePendingDelay`určuje, jak dlouho volající aplikace čeká na odpověď ze serveru před provedením další akce.

Obvykle jsou výchozí hodnoty přijatelné a není třeba je měnit. Rozhraní framework opakuje volání každý *nRetryReply* milisekund, dokud volání projde nebo zpoždění čekající na zprávu vypršela. Hodnota 0 pro *nRetryReply* určuje okamžité opakování a - 1 určuje zrušení volání.

Po vypršení zpoždění čekající na zprávu se zobrazí dialogové okno OLE "zaneprázdněn" (viz [COleBusyDialog),](../../mfc/reference/colebusydialog-class.md)aby se uživatel mohl rozhodnout zrušit nebo opakovat volání. Chcete-li povolit nebo zakázat toto dialogové okno, povolte nebo zakažte volání [enableBusyDialog.](#enablebusydialog)

Pokud během hovoru čeká na vyřízení na vyřízení zprávy klávesnice nebo myši a časový limit hovoru (překročil zpoždění čekající na zprávu), zobrazí se dialogové okno "neodpovídá". Volání [EnableNotRespondingDialog](#enablenotrespondingdialog) povolit nebo zakázat toto dialogové okno. Obvykle tento stav věcí naznačuje, že se něco pokazilo a uživatel je stále netrpělivý.

Pokud jsou dialogová okna zakázána, aktuální "opakovat odpověď" se vždy používá pro volání zaneprázdněné aplikace.

## <a name="see-also"></a>Viz také

[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)<br/>
[Graf hierarchie](../../mfc/hierarchy-chart.md)<br/>
[CCmdTarget – třída](../../mfc/reference/ccmdtarget-class.md)
