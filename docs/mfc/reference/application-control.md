---
title: Řízení aplikace
ms.date: 11/04/2016
helpviewer_keywords:
- application control [MFC]
ms.assetid: c1f69f15-e0fe-4515-9f36-d63d31869deb
ms.openlocfilehash: cb4ad19dfad06b793f226324d8e28c37c084ad67
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418900"
---
# <a name="application-control"></a>Řízení aplikace

Technologie OLE vyžaduje podstatnou kontrolu nad aplikacemi a jejich objekty. Systémové knihovny DLL systému OLE musí umožňovat automatické spouštění a vydávání aplikací, koordinaci jejich výroby a úprav objektů a tak dále. Funkce v tomto tématu splňují tyto požadavky. Kromě toho, že jsou tyto funkce volány pomocí knihoven DLL systému OLE, musí být někdy také volány aplikacemi.

### <a name="application-control"></a>Řízení aplikace

|||
|-|-|
|[AfxOleCanExitApp](#afxolecanexitapp)|Určuje, zda může aplikace skončit.|
|[AfxOleGetMessageFilter](#afxolegetmessagefilter)|Načte aktuální filtr zpráv aplikace.|
|[AfxOleGetUserCtrl](#afxolegetuserctrl)|Načte aktuální příznak uživatelského ovládacího prvku.|
|[AfxOleSetUserCtrl](#afxolesetuserctrl)|Nastaví nebo zruší příznak uživatelského ovládacího prvku.|
|[Funkci AfxOleLockApp](#afxolelockapp)|Zvýší globální počet aktivních objektů v aplikaci na číslo rozhraní.|
|[AfxOleLockControl](#afxolelockcontrol)| Zamkne objekt pro vytváření tříd určeného ovládacího prvku. |
|[Funkci AfxOleUnlockApp](#afxoleunlockapp)|Sníží počet aktivních objektů v aplikaci v rozhraní.|
|[AfxOleUnlockControl](#afxoleunlockcontrol)| Odemkne objekt pro vytváření tříd zadaného ovládacího prvku. |
|[AfxOleRegisterServerClass](#afxoleregisterserverclass)|Zaregistruje server v registru systému OLE.|
|[AfxOleSetEditMenu](#afxoleseteditmenu)|Implementuje uživatelské rozhraní pro příkaz objektu *TypeName* .|

##  <a name="afxolecanexitapp"></a>AfxOleCanExitApp

Určuje, zda může aplikace skončit.

```
BOOL AFXAPI AfxOleCanExitApp();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud aplikace může skončit; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Aplikace by neměla skončit, pokud existují nezpracované odkazy na její objekty. Globální funkce `AfxOleLockApp` a `AfxOleUnlockApp` přírůstku a snížením, v uvedeném pořadí, čítač odkazů na objekty aplikace. Aplikace by neměla skončit, pokud je tento čítač nenulový. Pokud je čítač nenulový, je hlavní okno aplikace skryté (nezničeno), když uživatel zvolí možnost Zavřít ze systémové nabídky nebo ukončit v nabídce soubor. Rozhraní volá tuto funkci v `CFrameWnd::OnClose`.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#2](../../mfc/codesnippet/cpp/application-control_1.cpp)]

## <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

##  <a name="afxolegetmessagefilter"></a>AfxOleGetMessageFilter

Načte aktuální filtr zpráv aplikace.

```
COleMessageFilter* AFXAPI AfxOleGetMessageFilter();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na aktuální filtr zpráv.

### <a name="remarks"></a>Poznámky

Voláním této funkce získáte přístup k aktuálnímu objektu odvozenému od `COleMessageFilter`stejným způsobem, jako byste volali `AfxGetApp` pro přístup k aktuálnímu objektu aplikace.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#3](../../mfc/codesnippet/cpp/application-control_2.cpp)]

[!code-cpp[NVC_MFCAutomation#4](../../mfc/codesnippet/cpp/application-control_3.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxwin. h

##  <a name="afxolegetuserctrl"></a>AfxOleGetUserCtrl

Načte aktuální příznak uživatelského ovládacího prvku.

```
BOOL AFXAPI AfxOleGetUserCtrl();
```

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je uživatel ovládacím prvkem aplikace; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Uživatel má řízení aplikace v případě, že uživatel explicitně otevřel nebo vytvořil nový dokument. Uživatel je také v ovládacím prvku řízení, pokud aplikace nebyla spuštěna pomocí knihoven DLL systému OLE – jinými slovy, pokud uživatel spustil aplikaci se systémovým prostředím.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

##  <a name="afxolesetuserctrl"></a>AfxOleSetUserCtrl

Nastaví nebo zruší příznak uživatelského ovládacího prvku, který je vysvětlen v odkazu pro `AfxOleGetUserCtrl`.

```
void AFXAPI AfxOleSetUserCtrl(BOOL bUserCtrl);
```

### <a name="parameters"></a>Parametry

*bUserCtrl*<br/>
Určuje, zda má být příznak ovládacího prvku uživatele nastaven nebo vymazán.

### <a name="remarks"></a>Poznámky

Rozhraní volá tuto funkci, když uživatel vytvoří nebo načte dokument, ale ne v případě, že je dokument načten nebo vytvořen pomocí nepřímé akce, jako je například načítání vloženého objektu z aplikace typu kontejner.

Tuto funkci volejte, pokud další akce v aplikaci by měly vložit uživatele do řízení aplikace.

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

##  <a name="afxolelockapp"></a>Funkci AfxOleLockApp

Zvýší globální počet aktivních objektů v aplikaci v rámci rozhraní.

```
void AFXAPI AfxOleLockApp();
```

### <a name="remarks"></a>Poznámky

Rozhraní udržuje počet aktivních objektů v aplikaci. Funkce `AfxOleLockApp` a `AfxOleUnlockApp`, v uvedeném pořadí, zvyšovat a snižovat tento počet.

Když se uživatel pokusí zavřít aplikaci, která má aktivní objekty – aplikace, pro kterou je počet aktivních objektů nenulový – rozhraní skrývá aplikaci ze zobrazení uživatele místo úplného vypínání. Funkce `AfxOleCanExitApp` určuje, zda může aplikace skončit.

Zavolejte `AfxOleLockApp` z libovolného objektu, který zveřejňuje rozhraní OLE, pokud by bylo nežádoucí pro tento objekt, který je zničen v době, kdy je stále používána klientská aplikace. Také zavolejte `AfxOleUnlockApp` v destruktoru libovolného objektu, který volá `AfxOleLockApp` v konstruktoru. Ve výchozím nastavení aplikace `COleDocument` (a odvozené třídy) automaticky uzamkne a odemkne aplikaci.

### <a name="example"></a>Příklad

[!code-cpp[NVC_MFCAutomation#5](../../mfc/codesnippet/cpp/application-control_4.cpp)]

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

##  <a name="afxoleunlockapp"></a>Funkci AfxOleUnlockApp

Sníží počet aktivních objektů v aplikaci v rozhraní.

```
void AFXAPI AfxOleUnlockApp();
```

### <a name="remarks"></a>Poznámky

Další informace najdete v tématu `AfxOleLockApp`.

Když počet aktivních objektů dosáhne nuly, je zavolána `AfxOleOnReleaseAllObjects`.

### <a name="example"></a>Příklad

Podívejte se na příklad pro [funkci AfxOleLockApp](#afxolelockapp).

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

## <a name="afxolelockcontrol"></a>AfxOleLockControl

Zamkne objekt pro vytváření tříd určeného ovládacího prvku, aby dynamicky vytvořená data přidružená k ovládacímu prvku zůstala v paměti.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleLockControl(  REFCLSID clsid  );
BOOL AFXAPI AfxOleLockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
Jedinečné ID třídy ovládacího prvku

*lpszProgID*<br/>
Jedinečné ID programu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt pro vytváření tříd ovládacího prvku úspěšně uzamčen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

To může výrazně zrychlit zobrazení ovládacích prvků. Když například vytvoříte ovládací prvek v dialogovém okně a zamknete ovládací prvek s `AfxOleLockControl`, nemusíte ho vytvářet a končit pokaždé, když se dialog zobrazí nebo zničí. Pokud uživatel opakovaně otevře a zavře dialogové okno, uzamykání ovládacích prvků může významně zvýšit výkon. Až budete připraveni na zničení ovládacího prvku, zavolejte `AfxOleUnlockControl`.

### <a name="example"></a>Příklad

```cpp
// Starts and locks control's (Microsoft Calendar) class factory.
// Control will remain in memory for lifetime of
// application or until AfxOleUnlockControl() is called.

AfxOleLockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

##  <a name="afxoleregisterserverclass"></a>AfxOleRegisterServerClass

Tato funkce umožňuje zaregistrovat server v registru systému OLE.

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

*CLSID*<br/>
Odkaz na ID třídy OLE serveru

*lpszClassName*<br/>
Ukazatel na řetězec obsahující název třídy objektů serveru.

*lpszShortTypeName*<br/>
Ukazatel na řetězec, který obsahuje krátký název typu objektu serveru, například "graf".

*lpszLongTypeName*<br/>
Ukazatel na řetězec obsahující dlouhý název typu objektu serveru, například graf Microsoft Excel 5,0.

*nAppType*<br/>
Hodnota, která je pořízena výčtem OLE_APPTYPE a určuje typ aplikace OLE. Možné hodnoty jsou následující:

- OAT_INPLACE_SERVER Server má úplné uživatelské rozhraní serveru.

- OAT_SERVER Server podporuje pouze vkládání.

- Kontejner OAT_CONTAINER podporuje odkazy na vložení.

- OAT_DISPATCH_OBJECT objektem podporujícím `IDispatch`.

*rglpszRegister*<br/>
Pole ukazatelů na řetězce představující klíče a hodnoty, které mají být přidány do systémového registru OLE, pokud nebyly nalezeny žádné existující hodnoty klíčů.

*rglpszOverwrite*<br/>
Pole ukazatelů na řetězce představující klíče a hodnoty, které mají být přidány do systémového registru OLE, pokud registr obsahuje existující hodnoty pro dané klíče.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud je třída serveru úspěšně registrována; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Většina aplikací může použít `COleTemplateServer::Register` k registraci typů dokumentů aplikace. Pokud formát systémového registru vaší aplikace nevyhovuje typickému vzoru, můžete použít `AfxOleRegisterServerClass` pro větší kontrolu.

Registr se skládá ze sady klíčů a hodnot. Argumenty *rglpszRegister* a *rglpszOverwrite* jsou pole ukazatelů na řetězce, z nichž každý se skládá z klíče a hodnoty oddělené znakem **null** (`'\0'`). Každý z těchto řetězců může mít nahraditelné parametry, jejichž umístění jsou označena znakovými sekvencemi *%1* až *%5*.

Symboly jsou vyplněny následujícím způsobem:

|Písmeno|Hodnota|
|------------|-----------|
|%1|ID třídy, formátovaný jako řetězec|
|%2|Název třídy|
|%3|Cesta ke spustitelnému souboru|
|%4|Krátký název typu|
|%5|Dlouhý název typu|

### <a name="requirements"></a>Požadavky

**Záhlaví**: afxdisp. h

##  <a name="afxoleseteditmenu"></a>AfxOleSetEditMenu

Implementuje uživatelské rozhraní pro příkaz objektu *TypeName* .

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

*pClient*<br/>
Ukazatel na položku klienta OLE.

*pMenu*<br/>
Ukazatel na objekt nabídky, který se má aktualizovat

*iMenuItem*<br/>
Index položky nabídky, která se má aktualizovat

*nIDVerbMin*<br/>
ID příkazu, které odpovídá primárnímu příkazu.

*nIDVerbMax*<br/>
ID příkazu odpovídající poslednímu příkazu.

*nIDConvert*<br/>
ID položky nabídky převést

### <a name="remarks"></a>Poznámky

Pokud server rozpozná pouze primární příkaz, položka nabídky se zobrazí jako "objekt *TypeName* pro příkaz" a příkaz *nIDVerbMin* se pošle, když uživatel zvolí příkaz. Pokud server rozpoznává několik příkazů, pak se položka nabídky bude " *TypeName* Object" a podnabídka, která obsahuje všechny operace, se zobrazí, když uživatel zvolí příkaz. Když uživatel zvolí příkaz z podnabídky, pošle se *nIDVerbMin* , pokud se vybere první příkaz, *nIDVerbMin* + 1 se pošle, pokud se vybere druhá operace, a tak dále. Výchozí implementace `COleDocument` tuto funkci automaticky zpracuje.

V skriptu prostředků aplikace klienta musíte mít následující příkaz (. RC):

**#include \<Afxolecl. RC >**

### <a name="requirements"></a>Požadavky

**Záhlaví**: AFXOLE. h

## <a name="afxoleunlockcontrol"></a>AfxOleUnlockControl

Odemkne objekt pro vytváření tříd zadaného ovládacího prvku.

### <a name="syntax"></a>Syntaxe

```
BOOL AFXAPI AfxOleUnlockControl( REFCLSID clsid );
BOOL AFXAPI AfxOleUnlockControl( LPCTSTR lpszProgID );
```

### <a name="parameters"></a>Parametry

*CLSID*<br/>
Jedinečné ID třídy ovládacího prvku

*lpszProgID*<br/>
Jedinečné ID programu ovládacího prvku.

### <a name="return-value"></a>Návratová hodnota

Nenulové, pokud byl objekt pro vytváření tříd ovládacího prvku úspěšně odemčen; v opačném případě 0.

### <a name="remarks"></a>Poznámky

Ovládací prvek je uzamčený pomocí `AfxOleLockControl`, aby dynamicky vytvořená data přidružená k ovládacímu prvku zůstala v paměti. To může výrazně zrychlit zobrazení ovládacího prvku, protože ovládací prvek nemusí být vytvořen a zničen při každém zobrazení. Až budete připraveni na zničení ovládacího prvku, zavolejte `AfxOleUnlockControl`.

### <a name="example"></a>Příklad

```cpp
// Unlock control's (Microsoft Calendar Control) class factory.

AfxOleUnlockControl(_T("MSCAL.Calendar"));
```

### <a name="requirements"></a>Požadavky

**Záhlaví:** afxwin. h

## <a name="see-also"></a>Viz také

[Makra a globální prvky](mfc-macros-and-globals.md)<br/>
