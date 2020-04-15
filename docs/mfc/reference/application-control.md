---
title: Řízení aplikace
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: 1f438d3344e90a16def2bd4c0f9cedcd47a64203
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363558"
---
# <a name="application-control"></a>Řízení aplikace

OLE vyžaduje podstatnou kontrolu nad aplikacemi a jejich objekty. Knihovny DLL systému OLE musí být schopny automaticky spouštět a vydávat aplikace, koordinovat jejich výrobu a úpravy objektů a tak dále. Funkce v tomto tématu splňují tyto požadavky. Kromě volání knihovních dll systému OLE musí být tyto funkce někdy volány také aplikacemi.

### <a name="application-control"></a>Řízení aplikace

|||
|-|-|
|[Aplikace AfxOleCanExitApp](#afxolecanexitapp)|Označuje, zda může být aplikace ukončena.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Načte aktuální filtr zpráv aplikace.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Načte aktuální příznak uživatelského ovládacího prvku.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Nastaví nebo vymaže příznak uživatelského ovládacího prvku.|
|[Aplikace AfxOleLockApp](#afxolelockapp)|Zintáží globální počet buněk rozhraní o počtu aktivních objektů v aplikaci.|
|[AfxOleLockControl](#afxolelockcontrol)| Uzamkne třídu výroby zadaného ovládacího prvku. |
|[Aplikace AfxOleUnlockApp](#afxoleunlockapp)|Sníží počet aktivních objektů v aplikaci v rámci.|
|[Ovládací prvek AfxOleUnlockControl](#afxoleunlockcontrol)| Odemkne třídy factory zadaného ovládacího prvku. |
|[Třída AfxOleRegisterServerClass](#afxoleregisterserverclass)|Zaregistruje server v systémovém registru OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementuje uživatelské rozhraní pro příkaz *typename* Object.|

## <a name="afxolecanexitapp"></a><a name="afxolecanexitapp"></a>Aplikace AfxOleCanExitApp

Označuje, zda může být aplikace ukončena.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud může být aplikace ukončena. jinak 0.

### <a name="remarks"></a>Poznámky

Aplikace by neměla být ukončena, pokud existují nevyřízené odkazy na její objekty. Globální funkce `AfxOleLockApp` `AfxOleUnlockApp` a přírůstek a snížení, v uvedeném pořadí, čítač odkazů na objekty aplikace. Aplikace by neměla být ukončena, pokud je tento čítač nenulový. Pokud je čítač nenulový, hlavní okno aplikace je skryté (není zničeno), když uživatel vybere Zavřít ze systémové nabídky nebo Ukončit z nabídky Soubor. Rozhraní Framework volá `CFrameWnd::OnClose`tuto funkci v aplikaci .

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="afxolegetmessagefilter"></a><a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Načte aktuální filtr zpráv aplikace.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální filtr zpráv.

### <a name="remarks"></a>Poznámky

Volání této funkce pro `COleMessageFilter`přístup k aktuální -odvozené `AfxGetApp` objektu, stejně jako byste volání pro přístup k aktuální mu objekt aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxwin.h

## <a name="afxolegetuserctrl"></a><a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Načte aktuální příznak uživatelského ovládacího prvku.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud má uživatel kontrolu nad aplikací; jinak 0.

### <a name="remarks"></a>Poznámky

Uživatel má kontrolu nad aplikací, když uživatel explicitně otevřel nebo vytvořil nový dokument. Uživatel je také pod kontrolou, pokud aplikace nebyla spuštěna OLE systém UD – jinými slovy, pokud uživatel spustil aplikaci se systémovým prostředím.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="afxolesetuserctrl"></a><a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Nastaví nebo vymaže příznak uživatelského ovládacího prvku, který je vysvětlen v odkazu pro `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parametry

*bUserCtrl*<br/>
Určuje, zda má být příznak uživatelského ovládacího prvku nastaven nebo vymazán.

### <a name="remarks"></a>Poznámky

Rozhraní Framework volá tuto funkci, když uživatel vytvoří nebo načte dokument, ale ne při načtení dokumentu nebo vytvoření prostřednictvím nepřímé akce, jako je například načtení vloženého objektu z aplikace kontejneru.

Volání této funkce, pokud jiné akce ve vaší aplikaci by měl dát uživateli pod kontrolou aplikace.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="afxolelockapp"></a><a name="afxolelockapp"></a>Aplikace AfxOleLockApp

Zintáží globální počet objektů v rámci počet aktivních objektů v aplikaci.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Poznámky

Rozhraní framework udržuje počet počet objektů aktivních v aplikaci. A `AfxOleLockApp` `AfxOleUnlockApp` funkce, respektive přírůstek a snížení tohoto počtu.

Když se uživatel pokusí zavřít aplikaci, která má aktivní objekty – aplikace, pro které počet aktivních objektů je nenulová – rozhraní skryje aplikaci z uživatelského zobrazení namísto úplného vypnutí. Funkce `AfxOleCanExitApp` označuje, zda může být aplikace ukončena.

Volání `AfxOleLockApp` z libovolného objektu, který zveřejňuje rozhraní OLE, pokud by nežádoucí pro tento objekt zničit při stále používá klientské aplikace. Také `AfxOleUnlockApp` volání v destruktoru libovolný `AfxOleLockApp` objekt, který volá v konstruktoru. Ve výchozím `COleDocument` nastavení (a odvozené třídy) automaticky uzamknout a odemknout aplikaci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="afxoleunlockapp"></a><a name="afxoleunlockapp"></a>Aplikace AfxOleUnlockApp

Sníží počet aktivních objektů v aplikaci v rámci.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Poznámky

Další `AfxOleLockApp` informace naleznete.

Když počet aktivních objektů dosáhne `AfxOleOnReleaseAllObjects` nuly, je volána.

### <a name="example"></a>Příklad

Viz příklad pro [AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Uzamkne třídu zadaného ovládacího prvku tak, aby dynamicky vytvořená data přidružená k ovládacímu prvku zůstala v paměti.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
Jedinečné ID třídy ovládacího prvku.

*lpszProgID*<br/>
Jedinečné ID programu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla továrna třídy ovládacího prvku úspěšně uzamčena; jinak 0.

### <a name="remarks"></a>Poznámky

To může výrazně urychlit zobrazení ovládacích prvků. Například po vytvoření ovládacího prvku v dialogovém `AfxOleLockControl`okně a uzamčení ovládacího prvku pomocí aplikace není nutné jej vytvářet a znovu ustupovat při každém zobrazení nebo zničení dialogového okna. Pokud uživatel otevře a zavře dialogové okno opakovaně, uzamčení ovládacích prvků může výrazně zvýšit výkon. Až budete připraveni zničit ovládací `AfxOleUnlockControl`prvek, zavolejte .

### <a name="example"></a>Příklad

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="afxoleregisterserverclass"></a><a name="afxoleregisterserverclass"></a>Třída AfxOleRegisterServerClass

Tato funkce umožňuje zaregistrovat server v systémovém registru OLE.

```
BOOL AFXAPI AfxOleRegisterServerClass(
    REFCLSID clsid,
    LPCTSTR lpszClassName,
    LPCTSTR lpszShortTypeName,
    LPCTSTR lpszLongTypeName,
    OLE_APPTYPE nAppType = OAT_SERVER,
    LPCTSTR* rglpszRegister = NULL,
    LPCTSTR* rglpszOverwrite = NULL);
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
Odkaz na ID třídy OLE serveru.

*název lpszClassName*<br/>
Ukazatel na řetězec obsahující název třídy objektů serveru.

*lpszShortTypeName*<br/>
Ukazatel na řetězec obsahující krátký název typu objektu serveru, například Graf.

*lpszLongTypeName*<br/>
Ukazatel na řetězec obsahující dlouhý název typu objektu serveru, například Graf aplikace Microsoft Excel 5.0.

*nTyp aplikace*<br/>
Hodnota převzatá z OLE_APPTYPE výčtu určující typ aplikace OLE. Možné hodnoty jsou následující:

- OAT_INPLACE_SERVER Server má úplné uživatelské rozhraní serveru.

- OAT_SERVER Server podporuje pouze vkládání.

- OAT_CONTAINER Container podporuje odkazy na vkládání.

- OAT_DISPATCH_OBJECT `IDispatch`objekt.

*rglpszRegistr*<br/>
Pole ukazatelů na řetězce představující klíče a hodnoty, které mají být přidány do systémového registru OLE, pokud nejsou nalezeny žádné existující hodnoty pro klíče.

*rglpszOverwrite*<br/>
Pole ukazatelů na řetězce představující klíče a hodnoty, které mají být přidány do systémového registru OLE, pokud registr obsahuje existující hodnoty pro dané klíče.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud je třída serveru úspěšně zaregistrována; jinak 0.

### <a name="remarks"></a>Poznámky

Většina aplikací `COleTemplateServer::Register` lze zaregistrovat typy dokumentů aplikace. Pokud formát systémového registru aplikace neodpovídá typickému vzoru, `AfxOleRegisterServerClass` můžete použít pro větší kontrolu.

Registr se skládá ze sady klíčů a hodnot. Argumenty *rglpszRegister* a *rglpszOverwrite* jsou pole ukazatelů na řetězce, z nichž každý se **NULL** skládá z `'\0'`klíče a hodnoty oddělené znakem NULL ( ). Každý z těchto řetězců může mít nahraditelné parametry, jejichž místa jsou označena sekvencemi znaků *%1* až *%5*.

Symboly se vyplňují takto:

|Symbol|Hodnota|
|------------|-----------|
|%1|ID třídy, formátované jako řetězec|
|%2|Název třídy|
|%3|Cesta ke spustitelnému souboru|
|%4|Krátký název typu|
|%5|Dlouhý název typu|

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp.h

## <a name="afxoleseteditmenu"></a><a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implementuje uživatelské rozhraní pro příkaz *typename* Object.

```
void AFXAPI AfxOleSetEditMenu(
    COleClientItem* pClient,
    CMenu* pMenu,
    UINT iMenuItem,
    UINT nIDVerbMin,
    UINT nIDVerbMax = 0,
    UINT nIDConvert = 0);
```

### <a name="parameters"></a>Parametry

*pKlient*<br/>
Ukazatel na položku OLE klienta.

*pNabídka*<br/>
Ukazatel na objekt nabídky, který má být aktualizován.

*položka iMenu*<br/>
Index položky nabídky, která má být aktualizována.

*nIDVerbMin*<br/>
ID příkazu, který odpovídá primární sloveso.

*nIDVerbMax*<br/>
ID příkazu, který odpovídá poslední sloveso.

*nIDConvert*<br/>
ID položky nabídky Převést

### <a name="remarks"></a>Poznámky

Pokud server rozpozná pouze primární sloveso, položka nabídky se stane *"typename* objektu slovesa" a příkaz *nIDVerbMin* je odeslán, když uživatel zvolí příkaz. Pokud server rozpozná několik sloves, pak se položka nabídky stane *"typename* Object" a podnabídka se seznamem všech sloves se zobrazí, když uživatel zvolí příkaz. Když uživatel vybere sloveso z podnabídky, *nIDVerbMin* je odeslán, pokud je vybránprvní sloveso, *nIDVerbMin* + 1 je odeslán, pokud je vybrán druhý sloveso, a tak dále. Výchozí `COleDocument` implementace automaticky zpracovává tuto funkci.

Ve skriptu prostředků aplikace klienta musí být následující příkaz (. RC) soubor:

**#include \<afxolecl.rc>**

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxole.h

## <a name="afxoleunlockcontrol"></a><a name="afxoleunlockcontrol"></a>Ovládací prvek AfxOleUnlockControl

Odemkne třídy factory zadaného ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*Identifikátor clsid*<br/>
Jedinečné ID třídy ovládacího prvku.

*lpszProgID*<br/>
Jedinečné ID programu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulová, pokud byla továrna třídy ovládacího prvku úspěšně odemčena; jinak 0.

### <a name="remarks"></a>Poznámky

Ovládací prvek je `AfxOleLockControl`uzamčen s , takže dynamicky vytvořená data spojená s ovládacím prvkem zůstane v paměti. To může výrazně urychlit zobrazení ovládacího prvku, protože ovládací prvek nemusí být vytvořen a zničen při každém zobrazení. Až budete připraveni zničit ovládací `AfxOleUnlockControl`prvek, zavolejte .

### <a name="example"></a>Příklad

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin.h

## <a name="see-also"></a>Viz také

[Makra a globální](mfc-macros-and-globals.md)<br/>
