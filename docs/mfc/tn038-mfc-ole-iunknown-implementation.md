---
title: 'TN038: Knihovny MFC-OLE – implementace třídy IUnknown'
ms.date: 06/28/2018
f1_keywords:
- vc.mfc.ole
helpviewer_keywords:
- aggregation macros [MFC]
- COM interfaces, base interface
- IUnknown interface
- END_INTERFACE_MAP macro [MFC]
- TN038
- BEGIN_INTERFACE_PART macro [MFC]
- DECLARE_INTERFACE_MAP macro [MFC]
- BEGIN_INTERFACE_MAP macro [MFC]
- OLE [MFC], implementing IUnknown interface
- METHOD_PROLOGUE macro [MFC]
- STDMETHOD macro [MFC]
- END_INTERFACE_PART macro [MFC]
- INTERFACE_PART macro
ms.assetid: 19d946ba-beaf-4881-85c6-0b598d7f6f11
ms.openlocfilehash: 0722ce294e6a088446b8ba681810cf3f7885f122
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62305473"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: MFC/OLE – implementace třídy IUnknown

> [!NOTE]
> Následující Technická poznámka nebyla aktualizována, protože byla poprvé zahrnuta v online dokumentaci. V důsledku toho některé postupy a témata mohou být nesprávné nebo zastaralé. Nejnovější informace se doporučuje vyhledat téma zájmu v dokumentaci online index.

V srdci objektu OLE 2 je "OLE Component Object Model" nebo COM. COM definuje standard pro jak spolupracující objekty komunikovat mezi sebou. Jedná se o jaké "objekt" vypadá, včetně jak metody se odesílají v objektu. COM také definuje základní třídu, ze které jsou odvozeny všechny třídy kompatibilní s com. Tato základní třída je [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). I když [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) rozhraní se označuje jako třída C++, COM není specifický pro žádný jazyk – se dá implementovat v jazyce C, PASCAL nebo jakéhokoli jiného jazyka, který podporuje binární rozložení objektu COM.

OLE se vztahuje na všechny třídy odvozené od [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) jako "rozhraní". Jde o důležité odlišení, protože "rozhraní" jako [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) nese s ním žádnou implementaci. Pouze definuje protokol, podle kterého objekty komunikují, ale nespecifikuje, co tyto implementace dělají. To je vhodné pro systém, který umožňuje maximální flexibilitu. Je úlohy MFC implementovat výchozí chování pro programy MFC/C++.

Pro pochopení implementace MFC atributu [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) musí nejprve porozumět, jaké je toto rozhraní. Zjednodušenou verzi [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) je definována níže:

```cpp
class IUnknown
{
public:
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj) = 0;
    virtual ULONG AddRef() = 0;
    virtual ULONG Release() = 0;
};
```

> [!NOTE]
> Podrobnosti o určité nezbytné konvenci volání, jako například `__stdcall` vynecháno pro tento obrázek.

[AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) členské funkce řídí správu paměti objektu. COM používá schéma součtu odkazů ke sledování objektů. Objektu nikdy odkazován přímo jako v jazyce C++. Místo toho jsou objekty COM vždy odkazovány prostřednictvím ukazatele. K uvolnění objektu, když vlastník se provádí pomocí jeho, objekt [Release](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) člen je volán (na rozdíl od použití operátoru delete, jako by se dělalo pro tradiční objekt jazyka C++). Mechanismus pro počítání referencí umožňuje správu více odkazů na jeden objekt. Implementace [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) udržuje počet odkazů na objekt – objekt není odstraněn, dokud jeho počet odkazů dosáhne nuly.

[AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) jsou z hlediska implementace poměrně jednoduché. Zde je triviální implementace:

```cpp
ULONG CMyObj::AddRef()
{
    return ++m_dwRef;
}

ULONG CMyObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}
```

[QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) členská funkce je o něco zajímavější. Není velmi výhodné disponovat objektem, jehož jedinými členskými funkcemi je [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) , bylo by dobré si objektu více příkazů, než [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) poskytuje. Tady [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) je užitečné. Umožňuje získat různá "rozhraní" na stejný objekt. Tato rozhraní jsou obvykle odvozena z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) a přidávají další funkce přidáním nových funkcí člena. Rozhraní COM nikdy nemají členské proměnné deklarované v rozhraní a všechny členské funkce jsou deklarovány jako čistě virtuální. Například

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Chcete získat IPrintInterface, pokud budete používat jen [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), volání [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) pomocí `IID` z `IPrintInterface`. `IID` Je 128bitové číslo, které rozhraní jedinečně identifikuje. Je `IID` pro každé rozhraní, které buď které OLE definuje. Pokud *pUnk* je ukazatel [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) objektu, může být kód k načtení IPrintInterface z něj:

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

Zdá se to být poměrně snadné, ale jak můžete implementovat objekt podporující IPrintInterface a [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) rozhraní v tomto případě je jednoduché vzhledem k tomu, že IPrintInterface je odvozen přímo z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) – implementací IPrintInterface je [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) je automaticky podporován. Příklad:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Implementace [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) budou naprosto stejné jako implementovanými výše. `CPrintObj::QueryInterface` bude vypadat přibližně takto:

```cpp
HRESULT CPrintObj::QueryInterface(REFIID iid, void FAR* FAR* ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = this;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}
```

Jak je vidět, pokud je identifikátor rozhraní (IID) rozpoznán, je vrácen ukazatel na váš objekt; v opačném případě dojde k chybě. Všimněte si také, úspěšného [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) vede k předpokládanému [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref). Samozřejmě je také třeba implementovat CEditObj::Print. To je jednoduché, protože IPrintInterface byla odvozena přímo z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) rozhraní. Nicméně, pokud jste chtěli podporu dvou různých rozhraní, obě odvozeny od [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), vezměte v úvahu následující:

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

I když existuje mnoho různých způsobů, jak implementovat třídu podporující rozhraní IEditInterface a IPrintInterface, včetně použití vícenásobné dědičnosti C++ tato poznámka se soustředí na používání vnořených tříd pro implementaci této funkce.

```cpp
class CEditPrintObj
{
public:
    CEditPrintObj();

    HRESULT QueryInterface(REFIID iid, void**);
    ULONG AddRef();
    ULONG Release();
    DWORD m_dwRef;

    class CPrintObj : public IPrintInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_printObj;

    class CEditObj : public IEditInterface
    {
    public:
        CEditPrintObj* m_pParent;
        virtual ULONG QueryInterface(REFIID iid, void** ppvObj);
        virtual ULONG AddRef();
        virtual ULONG Release();
    } m_editObj;
};
```

Celé provedení je zahrnuto níže:

```cpp
CEditPrintObj::CEditPrintObj()
{
    m_editObj.m_pParent = this;
    m_printObj.m_pParent = this;
}

ULONG CEditPrintObj::AddRef()
{
    return ++m_dwRef;
}

CEditPrintObj::Release()
{
    if (--m_dwRef == 0)
    {
        delete this;
        return 0;
    }
    return m_dwRef;
}

HRESULT CEditPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    if (iid == IID_IUnknown || iid == IID_IPrintInterface)
    {
        *ppvObj = &m_printObj;
        AddRef();
        return NOERROR;
    }
    else if (iid == IID_IEditInterface)
    {
        *ppvObj = &m_editObj;
        AddRef();
        return NOERROR;
    }
    return E_NOINTERFACE;
}

ULONG CEditPrintObj::CEditObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CEditObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CEditObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}

ULONG CEditPrintObj::CPrintObj::AddRef()
{
    return m_pParent->AddRef();
}

ULONG CEditPrintObj::CPrintObj::Release()
{
    return m_pParent->Release();
}

HRESULT CEditPrintObj::CPrintObj::QueryInterface(REFIID iid, void** ppvObj)
{
    return m_pParent->QueryInterface(iid, ppvObj);
}
```

Všimněte si, že většina [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) implementace je umístěn do třídy CEditPrintObj namísto duplikování kódu v CEditPrintObj::CEditObj a CEditPrintObj::CPrintObj. To snižuje množství kódu a zabraňuje chybám. Klíčovým bodem tedy je, že je možné volat z rozhraní IUnknown [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) Pokud chcete načíst tak libovolné rozhraní může objekt podporovat a z každého z těchto rozhraní je možné provádět to stejné. To znamená, že všechny [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkce z každého rozhraní se musí chovat přesně stejným způsobem. Aby tyto vložené objekty volaly implementaci ve "vnějším objektu" je ukazatel zpětného ukazatele používané (m_pParent). Během konstruktoru CEditPrintObj je inicializován ukazatel m_pParent. Pak byste implementovali také ceditprintobj::cprintobj:: Printobject a ceditprintobj::ceditobj:: také. Byl přidán poměrně kódu jednu funkci – možnost upravit objekt. Naštěstí je poměrně neobvyklé pro rozhraní, aby měly pouze jednu členskou funkci (i když k tomu dochází) a v takovém případě by EditObject a PrintObject obvykle byly sloučeny do jediného rozhraní.

To je velké množství vysvětlení a velké množství kódu pro tak jednoduchý scénář. Třídy MFC/OLE poskytují jednodušší alternativu. Implementace MFC používá techniku podobnou způsobu, jakým jsou zprávy Windows zabaleny s mapami zpráv. Toto zařízení se nazývá *mapy rozhraní* a je popsána v následující části.

## <a name="mfc-interface-maps"></a>Mapy rozhraní MFC

MFC/OLE obsahuje implementaci "Mapy rozhraní" podobné MFC "Mapy zprávy" a "Mapy odeslání" v pojetí a provedení. Základní funkce mapování rozhraní knihovny MFC jsou následující:

- Standardní implementace [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), integrované `CCmdTarget` třídy.

- Údržba počtu odkazů upravil [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref) a [vydání verze](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release)

- Implementace dat řízených [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_))

Kromě toho mapy rozhraní podporují následující rozšířené funkce:

- Podpora pro vytváření agregovatelných objektů COM

- Podpora pro používání agregovaných objektů v implementaci objektu COM.

- Implementace je připojitelná a rozšiřitelná

Další informace o agregaci naleznete v tématu [agregace](/windows/desktop/com/aggregation) tématu.

Podpora mapování rozhraní knihovny MFC je integrován `CCmdTarget` třídy. `CCmdTarget` "*a má*" referenční počet stejně jako všechny členské funkce přidružené [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) implementace (počet odkazů je například `CCmdTarget`). Chcete-li vytvořit třídu, která podporuje OLE COM, odvoďte třídu z `CCmdTarget` a použijte různá makra a členské funkce `CCmdTarget` k implementaci požadovaných rozhraní. Implementace MFC používá vnořené třídy pro definici jednotlivých implementací rozhraní, podobně jako v příkladu výše. Tím se usnadní pomocí standardní implementace IUnknown a počtu maker, které eliminují některý opakovaný kód.

## <a name="interface-map-basics"></a>Základy mapování rozhraní

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Jak implementovat třídu pomocí rozhraní MFC mapy

1. Přímo nebo nepřímo odvodit třídu z `CCmdTarget`.

2. Použití `DECLARE_INTERFACE_MAP` funkce v definici odvozené třídy.

3. Pro každé rozhraní, které chcete podporovat použijte BEGIN_INTERFACE_PART a END_INTERFACE_PART makra v definici třídy.

4. V souboru implementace pomocí makra BEGIN_INTERFACE_MAP a END_INTERFACE_MAP definovat mapování rozhraní třídy.

5. Pro každý podporovaný identifikátor IID použijte INTERFACE_PART – makro mezi BEGIN_INTERFACE_MAP a END_INTERFACE_MAP makra pro mapování daného IID na konkrétní "část" vaší třídy.

6. Implementace všech vnořených tříd, které představují rozhraní, které podporujete.

7. Použít pro přístup k nadřízenému METHOD_PROLOGUE – makro `CCmdTarget`-odvozenému objektu.

8. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), a [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) může delegovat `CCmdTarget` implementaci těchto funkcí (`ExternalAddRef`, `ExternalRelease`, a `ExternalQueryInterface`).

Může uvedený příklad CPrintEditObj je implementován takto:

```cpp
class CPrintEditObj : public CCmdTarget
{
public:
    // member data and member functions for CPrintEditObj go here

// Interface Maps
protected:
    DECLARE_INTERFACE_MAP()

    BEGIN_INTERFACE_PART(EditObj, IEditInterface)
        STDMETHOD_(void, EditObject)();
    END_INTERFACE_PART(EditObj)

    BEGIN_INTERFACE_PART(PrintObj, IPrintInterface)
        STDMETHOD_(void, PrintObject)();
    END_INTERFACE_PART(PrintObj)
};
```

Výše uvedené prohlášení vytvoří třídu odvozenou z `CCmdTarget`. DECLARE_INTERFACE_MAP – makro říká rozhraní framework, že tato třída bude mít vlastní mapu rozhraní. Kromě toho makra BEGIN_INTERFACE_PART a END_INTERFACE_PART definují vnořené třídy, v tomto případě s názvy CEditObj a CPrintObj (X slouží pouze k odlišení vnořených tříd od globálních tříd, které začíná "C" a rozhraní, třídy, které Začněte s "I"). Jsou vytvořeny dva vnoření členové těchto tříd: m_CEditObj a m_CPrintObj v uvedeném pořadí. Makra umožňují automaticky deklarovat [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), a [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkce; proto je pouze deklarovat pouze funkce specifické pro toto rozhraní: By EditObject a PrintObject (makro OLE se používá STDMETHOD tak, aby **_stdcall** a virtuální klíčová slova jsou k dispozici pro cílovou platformu podle potřeby).

Chcete-li implementovat mapu rozhraní pro tuto třídu:

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

To spojí IID_IPrintInterface IID s m_CPrintObj a IID_IEditInterface s m_CEditObj v uvedeném pořadí. `CCmdTarget` Provádění [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) (`CCmdTarget::ExternalQueryInterface`) používá tuto mapu k vrácení ukazatele do m_CPrintObj a m_CEditObj na požádání. Není nutné zahrnout položku pro `IID_IUnknown`; rámec použije první mapované rozhraní mapy (v tomto případě m_CPrintObj) při `IID_IUnknown` je požadováno.

I když BEGIN_INTERFACE_PART – makro automaticky deklarovalo [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release) a [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) funkce pro vás, je stále potřeba je implementovat:

```cpp
ULONG FAR EXPORT CEditPrintObj::XEditObj::AddRef()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalAddRef();
}

ULONG FAR EXPORT CEditPrintObj::XEditObj::Release()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return pThis->ExternalRelease();
}

HRESULT FAR EXPORT CEditPrintObj::XEditObj::QueryInterface(
    REFIID iid,
    void FAR* FAR* ppvObj)
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    return (HRESULT)pThis->ExternalQueryInterface(&iid, ppvObj);
}

void FAR EXPORT CEditPrintObj::XEditObj::EditObject()
{
    METHOD_PROLOGUE(CEditPrintObj, EditObj)
    // code to "Edit" the object, whatever that means...
}
```

Implementace CEditPrintObj::CPrintObj, bude nějak výše uvedenou definicí pro CEditPrintObj::CEditObj. I když by bylo možné vytvořit makro, které může použít k automatickému generování těchto funkcí (ale dříve při vývoji technologie MFC/OLE to byl tento případ), bude obtížné nastavit body přerušení, když makro vytvoří více než jeden řádek kódu. Z tohoto důvodu tento kód rozbalen ručně.

Pomocí implementace rozhraní mapování zpráv existuje několik věcí, které nebylo nezbytné učinit:

- Implementace QueryInterface

- Implementace AddRef a Release

- Deklarace některé z těchto vestavěných metod na obě vaše rozhraní

Kromě toho rozhraní používá interní mapy zpráv. Díky tomu lze odvodit z třídy systému, Řekněme, že `COleServerDoc`, která již podporuje určitá rozhraní a poskytuje náhrady nebo dodatky k rozhraním poskytovaným rozhraním. Můžete to provést, protože systém plně podporuje dědění mapy rozhraní ze základní třídy. To je důvod, proč BEGIN_INTERFACE_MAP bere jako svůj druhý parametr název základní třídy.

> [!NOTE]
> Obecně není možné znovu použít implementaci předdefinovaných implementací MFC rozhraní OLE pouhým zděděním vložené specializace rozhraní z verze MFC. To není možné protože použití METHOD_PROLOGUE – makro k získání přístupu do obsahujícího `CCmdTarget`-odvozené objekt implikuje *pevné odsazení* vloženého objektu z `CCmdTarget`-odvozenému objektu. To například znamená, že nemůžete odvodit vestavěnou vložený XMyAdviseSink z implementace MFC v `COleClientItem::XAdviseSink`, protože XAdviseSink spoléhá na to se v konkrétním odsazení od horní části `COleClientItem` objektu.

> [!NOTE]
> Můžete však delegovat do implementace MFC pro všechny funkce, které mají výchozí chování knihovny MFC. To se provádí v implementaci MFC `IOleInPlaceFrame` (XOleInPlaceFrame) v `COleFrameHook` třídy (deleguje se do m_xOleInPlaceUIWindow pro mnoho funkcí). Tento návrh byl zvolen ke zmenšení velikosti runtime objektů, které implementují mnoho rozhraní; To eliminuje potřebu ukazatel zpětného ukazatele (jako způsob m_pParent použitý v předchozí části).

### <a name="aggregation-and-interface-maps"></a>Agregace a mapy rozhraní

Kromě podpory samostatných objektů COM, MFC také podporuje agregaci. Agregace sama o sobě je příliš složité téma fattica. odkazovat [agregace](/windows/desktop/com/aggregation) tématu pro další informace o agregaci. Tato poznámka bude jednoduše popisovat podporu agregace integrované do mapy rozhraní framework a interface.

Existují dva způsoby použití agregace: (1) použití objektu COM, který podporuje agregaci a (2) implementace objektu, který může být agregovaný jiným. Tyto možnosti lze odkazovat jako "použití agregovaného objektu" a "nastavení objektu jako jako agregovatelného". MFC podporuje oboje.

### <a name="using-an-aggregate-object"></a>Použití agregovaného objektu

Chcete-li použít agregovaný objekt, musí existovat způsob, jak navázat agregát na mechanismus QueryInterface. Jinými slovy agregovaný objekt se musí chovat jako by šlo o nativní součást vašeho objektu. Jak se tento tie do mechanismu mapování rozhraní knihovny MFC kromě INTERFACE_PART – makro tam, kde vnořený objekt mapován na IID, můžete také deklarovat agregovaný objekt jako součást vaší `CCmdTarget` odvozené třídy. K tomu slouží makra INTERFACE_AGGREGATE. To vám umožní určit členskou proměnnou (která musí být ukazatel na [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) nebo odvozené třídy), které se mají být začleněny do mechanismu mapování rozhraní. Pokud ukazatel není NULL při `CCmdTarget::ExternalQueryInterface` je volána, rozhraní automaticky zavolá agregovaný objekt [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) členské funkce, pokud `IID` požadovaný není nativní `IID`s nepodporuje `CCmdTarget` samotného objektu.

#### <a name="to-use-the-interfaceaggregate-macro"></a>K použití makra interface_aggregate

1. Deklarace členské proměnné ( `IUnknown*`) která bude obsahovat ukazatel na agregovaný objekt.

2. Patří makra INTERFACE_AGGREGATE v mapě rozhraní odkazující na členskou proměnnou podle názvu.

3. V určitém okamžiku (obvykle během `CCmdTarget::OnCreateAggregates`), inicializuje členská proměnná na jinou hodnotu než NULL.

Příklad:

```cpp
class CAggrExample : public CCmdTarget
{
public:
    CAggrExample();

protected:
    LPUNKNOWN m_lpAggrInner;
    virtual BOOL OnCreateAggregates();

    DECLARE_INTERFACE_MAP()
    // "native" interface part macros may be used here
};

CAggrExample::CAggrExample()
{
    m_lpAggrInner = NULL;
}

BOOL CAggrExample::OnCreateAggregates()
{
    // wire up aggregate with correct controlling unknown
    m_lpAggrInner = CoCreateInstance(CLSID_Example,
        GetControllingUnknown(), CLSCTX_INPROC_SERVER,
        IID_IUnknown, (LPVOID*)&m_lpAggrInner);

    if (m_lpAggrInner == NULL)
        return FALSE;
    // optionally, create other aggregate objects here
    return TRUE;
}

BEGIN_INTERFACE_MAP(CAggrExample, CCmdTarget)
    // native "INTERFACE_PART" entries go here
    INTERFACE_AGGREGATE(CAggrExample, m_lpAggrInner)
END_INTERFACE_MAP()
```

Proměnná m_lpAggrInner je inicializována v konstruktoru na hodnotu NULL. Rámec ignoruje členskou proměnnou NULL ve výchozí implementaci [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). `OnCreateAggregates` je vhodné místo pro vytvoření skutečných agregovaných objektů. Bude nutné jej volat explicitně, pokud vytváříte objekt mimo implementaci MFC `COleObjectFactory`. Důvod vytvoření agregace v `CCmdTarget::OnCreateAggregates` a využití `CCmdTarget::GetControllingUnknown` se stane při vytváření agregovatelných objektů je popsána zřejmý.

Tato technika vám poskytne vašemu objektu všechna rozhraní, která agregovaný objekt podporuje, a jeho nativní rozhraní. Pokud chcete pouze podmnožinu rozhraní, která podporuje agregace, můžete přepsat `CCmdTarget::GetInterfaceHook`. To vám umožní hookability velmi nízké úrovni, podobné [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)). Obvykle chcete všechna rozhraní, která podporuje agregace.

### <a name="making-an-object-implementation-aggregatable"></a>Vytváření agregovatelných implementace objektu

Pro objekt chcete umožnit možnost agregace, provádění [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), a [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) musí delegovat na "řídící Neznámá". Jinými slovy, aby se jednat o část objektu, je třeba delegovat [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), a [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) na jiný objekt, také odvozený z [ IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). Tato "řídící Neznámá" je k dispozici na objekt při jeho vytvoření, to znamená, je poskytována pro implementaci `COleObjectFactory`. Tato implementace provede malé množství režie a v některých případech není žádoucí, takže knihovny MFC volitelné. Chcete-li umožnit možnost agregace objektu, volejte `CCmdTarget::EnableAggregation` z konstruktoru objektu.

Pokud objekt také používá agregace, musíte být také potřeba správný průchod "řídící Neznámá" pro agregaci objektů. Obvykle to [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) ukazatel je předán do objektu při vytvoření agregace. Například parametr pUnkOuter je "řídící Neznámá" pro objekty vytvořené pomocí `CoCreateInstance`. Správný ukazatel "řídící Neznámá" může být načten voláním `CCmdTarget::GetControllingUnknown`. Hodnota vrácená z této funkce však není během sestavování konstruktoru. Z tohoto důvodu doporučujeme vytvořit vaše agregace pouze v přepsání `CCmdTarget::OnCreateAggregates`, kde návratová hodnota z `GetControllingUnknown` je spolehlivá, i v případě vytvoření z `COleObjectFactory` implementace.

Je také důležité, že objekt manipuluje počtem správných odkazů při přidávání nebo uvolnění počtů umělých odkazů. Aby to platí vždy volat `ExternalAddRef` a `ExternalRelease` místo `InternalRelease` a `InternalAddRef`. Zřídka dochází k volání `InternalRelease` nebo `InternalAddRef` na třídu, která podporuje agregace.

## <a name="reference-material"></a>Referenční materiál

Pokročilé použití OLE, jako je definování vlastního rozhraní nebo přepsání implementace rozhraní OLE, vyžaduje použití základního mechanismu mapování rozhraní.

Tato část popisuje jednotlivá makra a rozhraní API, která se používá k implementaci těchto rozšířených funkcí.

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget::EnableAggregation – Popis funkce

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>Poznámky

Voláním této funkce v konstruktoru odvozené třídy, pokud si přejete podporovat agregace OLE pro objekty tohoto typu. To připraví speciální implementaci IUnknown, která je požadována pro agregovatelné objekty.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget::ExternalQueryInterface – Popis funkce

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>Parametry

*lpIID*<br/>
Vzdálenější ukazatel na IID (první argument funkce QueryInterface)

*ppvObj*<br/>
Ukazatel rozhraní IUnknown * (druhý argument funkce QueryInterface)

#### <a name="remarks"></a>Poznámky

Volejte tuto funkce ve vaší implementaci IUnknown pro každé rozhraní vaše třída implementuje. Tato funkce poskytuje standardní řízené daty implementaci QueryInterface na základě mapy rozhraní objektu. Je nezbytné převést vrácenou hodnotu na HRESULT. Pokud objekt je agregován, tato funkce bude volat "Řízení IUnknown" namísto použití místní mapu rozhraní.

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget::ExternalAddRef – Popis funkce

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>Poznámky

Volejte tuto funkce ve vaší implementaci IUnknown::addref pro každé rozhraní vaše třída implementuje. Vrácená hodnota je nový počet odkazů na objekt CCmdTarget. Pokud objekt je agregován, tato funkce bude volat "Řízení IUnknown" bez nutnosti manipulovat počet místních odkazů.

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget::ExternalRelease – Popis funkce

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>Poznámky

Volejte tuto funkce ve vaší implementaci IUnknown::Release pro každé rozhraní vaše třída implementuje. Návratová hodnota označuje nový počet odkazů na objekt. Pokud objekt je agregován, tato funkce bude volat "Řízení IUnknown" bez nutnosti manipulovat počet místních odkazů.

### <a name="declareinterfacemap--macro-description"></a>DECLARE_INTERFACE_MAP – Popis makra

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Poznámky

Použijte toto makro v libovolné třídě odvozené z `CCmdTarget` , který bude mít mapování rozhraní. Používá se téměř stejným způsobem jako DECLARE_MESSAGE_MAP. Vyvolání toto makra by mělo být umístěno definici třídy, obvykle v záhlaví (. H) file. Třída s atributem DECLARE_INTERFACE_MAP musí definovat mapování rozhraní v souboru implementace (. CPP) s makry BEGIN_INTERFACE_MAP a END_INTERFACE_MAP.

### <a name="begininterfacepart-and-endinterfacepart--macro-descriptions"></a>BEGIN_INTERFACE_PART a END_INTERFACE_PART – popisy makra

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>Parametry

*localClass*<br/>
Název třídy, která implementuje rozhraní

*iface*<br/>
Název, který tato třída implementuje rozhraní

#### <a name="remarks"></a>Poznámky

Pro každé rozhraní, které implementuje vaše třída musíte mít pár BEGIN_INTERFACE_PART a END_INTERFACE_PART. Tato makra definují lokální třídu odvozenou z rozhraní OLE, které definujete, a z vložené členské proměnné této třídy. [AddRef](/windows/desktop/api/unknwn/nf-unknwn-iunknown-addref), [vydání](/windows/desktop/api/unknwn/nf-unknwn-iunknown-release), a [QueryInterface](/windows/desktop/api/unknwn/nf-unknwn-iunknown-queryinterface(q_)) členy jsou deklarováni automaticky. Musíte zahrnout deklarace ostatních funkcí členů, které jsou součástí implementovaného rozhraní (tyto deklarace jsou umístěny mezi BEGIN_INTERFACE_PART a END_INTERFACE_PART makra).

*Iface* rozhraní OLE, které chcete implementovat, jako je argument `IAdviseSink`, nebo `IPersistStorage` (nebo vlastní rozhraní).

*LocalClass* argumentem je název místní třídy, která bude obsahovat definici. "X" bude automaticky předsunuto před název. Tato konvence pojmenování se používá pro zabránění kolizím s globálními třídami se stejným názvem. Navíc název vloženého člena, stejný jako *localClass* název s výjimkou předchází "m_x".

Příklad:

```cpp
BEGIN_INTERFACE_PART(MyAdviseSink, IAdviseSink)
    STDMETHOD_(void, OnDataChange)(LPFORMATETC, LPSTGMEDIUM);
    STDMETHOD_(void, OnViewChange)(DWORD, LONG);
    STDMETHOD_(void, OnRename)(LPMONIKER);
    STDMETHOD_(void, OnSave)();
    STDMETHOD_(void, OnClose)();
END_INTERFACE_PART(MyAdviseSink)
```

bude definovat místní třídu nazvanou myadvisesink z IAdviseSink a členem třídy, ve kterém je deklarován, nazvané m_xmyadvisesink. Poznámka:

> [!NOTE]
> Řádky začínající textem `STDMETHOD`_ jsou v podstatě kopírovány z OLE2. H a mírně upraveny. Kopírování z OLE2. H můžete snížit počet chyb, které se těžko řeší.

### <a name="begininterfacemap-and-endinterfacemap--macro-descriptions"></a>BEGIN_INTERFACE_MAP a END_INTERFACE_MAP – popisy makra

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ve kterém má definovat mapa rozhraní

*baseClass*<br/>
Třída, ze které *theClass* odvozena.

#### <a name="remarks"></a>Poznámky

BEGIN_INTERFACE_MAP a END_INTERFACE_MAP makra se používají v souboru implementace skutečnou definici mapy rozhraní. Pro každé rozhraní, která je implementována je jeden nebo více vyvoláním makra INTERFACE_PART. Pro každou agregaci, která používá třídu je jedna volání makra INTERFACE_AGGREGATE.

### <a name="interfacepart--macro-description"></a>INTERFACE_PART — Popis makra

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy, která obsahuje mapu rozhraní.

*iid*<br/>
`IID` , Který se má namapovat na vloženou třídu.

*localClass*<br/>
Název místní třídy (menší než "X").

#### <a name="remarks"></a>Poznámky

Toto makro se používá mezi – makro BEGIN_INTERFACE_MAP a END_INTERFACE_MAP – makro pro každé rozhraní, které bude váš objekt podporovat. Umožňuje mapovat IID ke členovi třídy podle *theClass* a *localClass*. "m_x" se přidají do *localClass* automaticky. Všimněte si, že více než jeden `IID` může být spojen s jeden člen. To je velmi užitečné, když implementujete pouze "nejvíce odvozené" rozhraní a chcete poskytnout také všechna mezilehlá rozhraní. Dobrým příkladem tohoto je `IOleInPlaceFrameWindow` rozhraní. Jeho hierarchie vypadá takto:

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

Pokud objekt implementuje `IOleInPlaceFrameWindow`, klient může `QueryInterface` na kterékoli z těchto rozhraní: `IOleUIWindow`, `IOleWindow`, nebo [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown), kromě "nejvíce odvozeného" rozhraní `IOleInPlaceFrameWindow` (ten se ve skutečnosti implementace). Chcete-li se o to postarají můžete použít více než jeden INTERFACE_PART – makro mapovat každého základního rozhraní na `IOleInPlaceFrameWindow` rozhraní:

v souboru definice třídy:

```cpp
BEGIN_INTERFACE_PART(CMyFrameWindow, IOleInPlaceFrameWindow)
```

v souboru implementace třídy:

```cpp
BEGIN_INTERFACE_MAP(CMyWnd, CFrameWnd)
    INTERFACE_PART(CMyWnd, IID_IOleWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleUIWindow, MyFrameWindow)
    INTERFACE_PART(CMyWnd, IID_IOleInPlaceFrameWindow, MyFrameWindow)
END_INTERFACE_MAP
```

Rámec pečuje o IUnknown vzhledem k tomu, že je vždy vyžadován.

### <a name="interfacepart--macro-description"></a>INTERFACE_PART — Popis makra

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy, která obsahuje mapu rozhraní

*theAggr*<br/>
Název členské proměnné, která se dají agregovat.

#### <a name="remarks"></a>Poznámky

Toto makro se používá k informování rozhraní framework, že třída používá agregovaný objekt. Musí být mezi BEGIN_INTERFACE_PART a END_INTERFACE_PART makra. Agregovaný objekt je samostatný objekt, odvozený z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown). Pomocí agregace a makra INTERFACE_AGGREGATE můžete nastavit všechna rozhraní, která agregace podporuje zdá se být přímo podporována objektem. *TheAggr* argument je jednoduše název proměnné člena vaší třídy, který je odvozen z [IUnknown](/windows/desktop/api/unknwn/nn-unknwn-iunknown) (přímo nebo nepřímo). Všechna makra INTERFACE_AGGREGATE musí následovat makra INTERFACE_PART při umístění v mapě rozhraní.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
