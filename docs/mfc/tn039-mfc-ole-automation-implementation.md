---
title: 'TN039: MFC-OLE – implementace automatizace'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- MFC, COM support
- IDispatch interface
- MFC, OLE DB and
- TN039
- Automation, MFC COM interface entry points
ms.assetid: 765fa3e9-dd54-4f08-9ad2-26e0546ff8b6
ms.openlocfilehash: cd6f8d681ef7e6517f2172ca6b22b13723a962fd
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50658985"
---
# <a name="tn039-mfcole-automation-implementation"></a>TN039: MFC/OLE – implementace automatizace

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

## <a name="overview-of-ole-idispatch-interface"></a>Přehled rozhraní IDispatch OLE

`IDispatch` Rozhraní se prostředky, pomocí kterého aplikace zpřístupnit metody a vlastnosti, které můžete provést další aplikace, jako je například Visual BASIC nebo jiné jazyky, pomocí funkcí aplikace. Je nejdůležitější část tohoto rozhraní `IDispatch::Invoke` funkce. Knihovna MFC používá "mapy odeslání" pro implementaci `IDispatch::Invoke`. Mapa odbavení poskytuje informace o implementaci MFC na rozložení nebo "tvar" vaší `CCmdTarget`-odvozené třídy, takže ho můžete přímo pracovat s vlastností objektu, nebo volat členské funkce v rámci objektu splňovat `IDispatch::Invoke` požadavky.

Ve většině případů ClassWizard a MFC spolupracují, aby skrýt nejvíce podrobností OLE automation z programátor aplikace. Programátor se soustřeďuje na skutečná funkce k vystavení v aplikaci a nemá se starat o podkladové zajistí funkčnost systému.

Existují případy, ale, kde je potřeba pochopit, co dělá MFC na pozadí. Tato poznámka bude zabývat přiřazování rozhraní **DISPID**s členské funkce a vlastnosti. Znalost algoritmus knihovna MFC používá pro přiřazení **DISPID**s je potřeba, pouze když budete potřebovat znát ID, jako je například při vytváření knihovny typů"" pro objekty vaší aplikace.

## <a name="mfc-dispid-assignment"></a>Přiřazení DISPID knihovny MFC

I když koncový uživatel automatizace (Visual Basic uživatele, například), se zobrazí skutečné názvy automatizace povolené vlastnostem a metodám v kódu (jako je například knihovna ShowWindow), provádění `IDispatch::Invoke` neobdrží skutečné názvy. Z důvodu optimalizace přijme **DISPID**, což je 32-bit "magic soubor cookie", který popisuje metody nebo vlastnosti, která je přístupná. Tyto **DISPID** hodnoty jsou vráceny z `IDispatch` implementaci prostřednictvím další metodu s názvem `IDispatch::GetIDsOfNames`. Aplikace klienta automatizace zavolá `GetIDsOfNames` jednou pro každého člena nebo vlastnost se chystá pro přístup k a mezipaměti pro pozdější volání `IDispatch::Invoke`. Tímto způsobem, vyhledávací řetězec nákladné stačí jednou za použití objektu, namísto jednou za `IDispatch::Invoke` volání.

Určuje MFC **DISPID**s pro jednotlivé metody a vlastnosti podle dvě věci:

- Vzdálenost od horní části mapy odeslání (1 relativní)

- Vzdálenost mapa odeslání mezi nejvíce odvozenou třídou (relativní 0)

**DISPID** je rozdělena na dva oddíly. **LOWORD** z **DISPID** obsahuje první součást, vzdálenost od horní části mapy odeslání. **HIWORD** obsahuje vzdálenost od nejvíce odvozené třídy. Příklad:

```cpp
class CDispPoint : public CCmdTarget
{
public:
    short m_x, m_y;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

class CDisp3DPoint : public CDispPoint
{
public:
    short m_z;
    // ...
    DECLARE_DISPATCH_MAP()
    // ...
};

BEGIN_DISPATCH_MAP(CDispPoint, CCmdTarget)
    DISP_PROPERTY(CDispPoint, "x", m_x, VT_I2)
    DISP_PROPERTY(CDispPoint, "y", m_y, VT_I2)
END_DISPATCH_MAP()

BEGIN_DISPATCH_MAP(CDisp3DPoint, CDispPoint)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
END_DISPATCH_MAP()
```

Jak je vidět, existují dvě třídy, které zveřejňují rozhraní automatizace OLE. Jedna z těchto tříd je odvozena od druhé a proto využívá funkce základní třídy, včetně součástí automatizace OLE ("x" a "y" vlastnosti v tomto případě).

Bude generovat MFC **DISPID**s pro třídy CDispPoint následujícím způsobem:

```cpp
property X    (DISPID)0x00000001
property Y    (DISPID)0x00000002
```

Protože vlastnosti nejsou v základní třídě, **HIWORD** z **DISPID** je vždy nula (vzdálenost od nejvíce odvozené třídy pro CDispPoint je nula).

Bude generovat MFC **DISPID**s pro třídy CDisp3DPoint následujícím způsobem:

```cpp
property Z    (DISPID)0x00000001
property X    (DISPID)0x00010001
property Y    (DISPID)0x00010002
```

Z vlastnosti je předána **DISPID** nulu na začátku **HIWORD** vzhledem k tomu, že je definován ve třídě, která vystavuje vlastnosti CDisp3DPoint. Protože vlastnosti X a Y jsou definovány v základní třídě, **HIWORD** z **DISPID** je 1, protože je třída, ve kterém jsou tyto vlastnosti definované ve vzdálenosti jeden odvození od nejvíce odvozené třídy.

> [!NOTE]
> **LOWORD** je vždy určena podle pozice v objektu map, i v případě, že existují položky v objektu map s explicitní **DISPID** (Další informace naleznete na **_ID** verze `DISP_PROPERTY` a `DISP_FUNCTION` makra).

## <a name="advanced-mfc-dispatch-map-features"></a>Pokročilé funkce mapy odbavení knihovny MFC

Existuje mnoho dalších funkcí, které ClassWizard nepodporuje v této verzi aplikace Visual C++. Podporuje ClassWizard `DISP_FUNCTION`, `DISP_PROPERTY`, a `DISP_PROPERTY_EX` který definovat v uvedeném pořadí – metoda, vlastnost proměnné člena a get/set členských funkcí vlastností. Tyto možnosti jsou obvykle vše, co je potřeba k vytvoření většina automatizační servery.

Následující další makra se dá použít při ClassWizard podporována makra nejsou adekvátní: `DISP_PROPERTY_NOTIFY`, a `DISP_PROPERTY_PARAM`.

## <a name="disppropertynotify--macro-description"></a>DISP_PROPERTY_NOTIFY – Popis makro

```cpp
DISP_PROPERTY_NOTIFY(
    theClass,
    pszName,
    memberName,
    pfnAfterSet,
    vtPropType)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy.

*pszName*<br/>
Externí název vlastnosti.

*Jméno*<br/>
Název členské proměnné, ve kterém je uložené vlastnosti.

*pfnAfterSet*<br/>
Název členská funkci volat, když je změněna vlastnost.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

### <a name="remarks"></a>Poznámky

Toto makro je mnohem jako DISP_PROPERTY, s tím rozdílem, že přijímá další argument. Další argument *pfnAfterSet,* musí být členská funkce, která nic nespouští a nepřijímá žádné parametry "void OnPropertyNotify()". Bude volána **po** členská proměnná byla změněna.

## <a name="disppropertyparam--macro-description"></a>DISP_PROPERTY_PARAM – Popis makro

```cpp
DISP_PROPERTY_PARAM(
    theClass,
    pszName,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy.

*pszName*<br/>
Externí název vlastnosti.

*memberGet*<br/>
Název členské funkce použít k získání vlastnosti.

*Členů*<br/>
Název členské funkce lze nastavit vlastnost.

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

*vtsParams*<br/>
Řetězec místo oddělených VTS_ pro každý parametr.

### <a name="remarks"></a>Poznámky

Podobně jako DISP_PROPERTY_EX – makro toto makro definuje vlastnost s zvláštní členské funkce Get a Set. Toto makro, ale umožňuje určit seznam parametrů pro vlastnost. To je užitečné pro implementaci vlastnosti, které jsou indexována nebo parametrizované jiným způsobem. Parametry budou vždy umístěny nejprve, za nímž následuje novou hodnotu pro vlastnost. Příklad:

```cpp
DISP_PROPERTY_PARAM(CMyObject, "item", GetItem, SetItem, VT_DISPATCH, VTS_I2 VTS_I2)
```

odpovídá get i set členské funkce:

```cpp
LPDISPATCH CMyObject::GetItem(short row, short col)
void CMyObject::SetItem(short row, short col, LPDISPATCH newValue)
```

## <a name="dispxxxxid--macro-descriptions"></a>DISP_XXXX_ID – Popisy makra

```cpp
DISP_FUNCTION_ID(
    theClass,
    pszName,
    dispid,
    pfnMember,
    vtRetVal,
    vtsParams)
DISP_PROPERTY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    vtPropType)
DISP_PROPERTY_NOTIFY_ID(
    theClass,
    pszName,
    dispid,
    memberName,
    pfnAfterSet,
    vtPropType)
DISP_PROPERTY_EX_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType)
DISP_PROPERTY_PARAM_ID(
    theClass,
    pszName,
    dispid,
    pfnGet,
    pfnSet,
    vtPropType,
    vtsParams)
```

### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy.

*pszName*<br/>
Externí název vlastnosti.

*identifikátor DISPID*<br/>
Pevná hodnota DISPID pro vlastnosti nebo metody.

*pfnGet*<br/>
Název členské funkce použít k získání vlastnosti.

*pfnSet*<br/>
Název členské funkce lze nastavit vlastnost.

*Jméno*<br/>
Název členské proměnné pro mapování na vlastnost

*vtPropType*<br/>
Hodnota určující typ vlastnosti.

*vtsParams*<br/>
Řetězec místo oddělených VTS_ pro každý parametr.

### <a name="remarks"></a>Poznámky

Tato makra umožňují zadat **DISPID** místo MFC automaticky přiřadí. Mezi Tato upřesňující makra mají stejné názvy, s výjimkou tohoto ID se připojí název makra (třeba **DISP_PROPERTY_ID**) a ID se určuje podle parametru určeného hned za *pszName* parametr. Zobrazit AFXDISP. Další informace o těchto makrech H. **_ID** položky musí být umístěny na konci mapa odeslání. Bude mít vliv na automatické **DISPID** generování stejným způsobem jako non -**_ID** by verze makra ( **DISPID**s jsou určeny umístěním). Příklad:

```cpp
BEGIN_DISPATCH_MAP(CDisp3DPoint, CCmdTarget)
    DISP_PROPERTY(CDisp3DPoint, "y", m_y, VT_I2)
    DISP_PROPERTY(CDisp3DPoint, "z", m_z, VT_I2)
    DISP_PROPERTY_ID(CDisp3DPoint, "x", 0x00020003, m_x, VT_I2)
END_DISPATCH_MAP()
```

MFC vygeneruje hodnoty dispID pro třídu CDisp3DPoint následujícím způsobem:

```cpp
property X    (DISPID)0x00020003
property Y    (DISPID)0x00000002
property Z    (DISPID)0x00000001
```

Určení pevnou **DISPID** je užitečné pro zachování zpětné kompatibility na dříve existující rozhraní odbavení, jak implementovat určité vlastnosti nebo metody definovaná systémem (obvykle indikován záporné  **Identifikátor DISPID**, například **konstantu DISPID_NEWENUM** kolekce).

## <a name="retrieving-the-idispatch-interface-for-a-coleclientitem"></a>Načítání rozhraní IDispatch pro COleClientItem

Mnoho serverů bude podporovat automation v rámci své objekty dokumentu, spolu s funkcemi serveru OLE. Aby bylo možné získat přístup k tomuto rozhraní automatizace, je potřeba přímý přístup `COleClientItem::m_lpObject` členské proměnné. Následující kód načte `IDispatch` rozhraní pro objekt odvozený od `COleClientItem`. Pokud tuto funkci najít potřebné, můžete do aplikace zahrnout níže uvedený kód:

```cpp
LPDISPATCH CMyClientItem::GetIDispatch()
{
    ASSERT_VALID(this);
    ASSERT(m_lpObject != NULL);

    LPUNKNOWN lpUnk = m_lpObject;

    Run();      // must be running

    LPOLELINK lpOleLink = NULL;
    if (m_lpObject->QueryInterface(IID_IOleLink,
        (LPVOID FAR*)&lpOleLink) == NOERROR)
    {
        ASSERT(lpOleLink != NULL);
        lpUnk = NULL;
        if (lpOleLink->GetBoundSource(&lpUnk) != NOERROR)
        {
            TRACE0("Warning: Link is not connected!\n");
            lpOleLink->Release();
            return NULL;
        }
        ASSERT(lpUnk != NULL);
    }

    LPDISPATCH lpDispatch = NULL;
    if (lpUnk->QueryInterface(IID_IDispatch, &lpDispatch) != NOERROR)
    {
        TRACE0("Warning: does not support IDispatch!\n");
        return NULL;
    }

    ASSERT(lpDispatch != NULL);
    return lpDispatch;
}
```

Rozhraní odbavení vrácená z této funkce pak může použít přímo nebo připojené k `COleDispatchDriver` pro typově bezpečný přístup. Když ho používáte přímo, ujistěte se, že je potřeba volat jeho `Release` člen při přes ukazatel ( `COleDispatchDriver` destruktor se k tomu ve výchozím nastavení).

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
