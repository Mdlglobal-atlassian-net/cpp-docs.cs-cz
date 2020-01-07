---
title: 'TN038: MFC-OLE – implementace rozhraní IUnknown'
ms.date: 06/28/2018
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
ms.openlocfilehash: 9ceb903ec38bc0ad7cfdee1c59babd2379422ac3
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/20/2019
ms.locfileid: "75302351"
---
# <a name="tn038-mfcole-iunknown-implementation"></a>TN038: MFC/OLE – implementace třídy IUnknown

> [!NOTE]
> Následující technická Poznámka nebyla od prvního zařazení do online dokumentace aktualizována. V důsledku toho mohou být některé postupy a témata neaktuální nebo nesprávné. Nejnovější informace najdete v tématu informace o tom, co je důležité v online katalogu dokumentace najít.

Na srdci OLE 2 je "objektový model komponenty OLE" nebo COM. Model COM definuje standard pro spolupráci vzájemně komunikujících objektů. To zahrnuje podrobné informace o tom, co vypadá "Object", včetně způsobu, jakým jsou metody odesílány u objektu. Model COM také definuje základní třídu, ze které jsou odvozeny všechny třídy kompatibilní s modelem COM. Tato základní třída je [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). I když je rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) odkazováno jako C++ třída, com není specifické pro žádný jazyk – může být implementováno v jazyce C, Pascal nebo v jakémkoli jiném jazyce, který může podporovat binární rozložení objektu com.

OLE odkazuje na všechny třídy odvozené z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) jako "rozhraní". Jedná se o důležité rozlišení, protože "rozhraní", jako je [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , provádí bez implementace. Jednoduše definuje protokol, pomocí kterého objekty komunikují, nikoli specifiky toho, co tyto implementace dělají. To je přijatelné pro systém, který umožňuje maximální flexibilitu. Je to úloha knihovny MFC pro implementaci výchozího chování pro MFC/C++ programy.

Aby bylo možné pochopit implementaci rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) knihovny MFC, je nutné nejprve pochopit, co je toto rozhraní. Zjednodušená verze [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) je definována níže:

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
> Některé nezbytné podrobnosti o konvenci volání, například `__stdcall`, jsou pro tento obrázek vynechány.

Členské funkce [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) řídí správu paměti objektu. Model COM používá schéma počítání odkazů k udržení přehledu o objektech. Na objekt nikdy neodkazuje přímo jako v C++. Místo toho jsou objekty COM vždy odkazovány prostřednictvím ukazatele. Chcete-li uvolnit objekt, když je jeho vlastník proveden pomocí, je volán člen [verze](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) objektu (na rozdíl od použití operátoru delete, jak by byl proveden pro tradiční C++ objekt). Mechanismus počítání odkazů umožňuje spravovat více odkazů na jeden objekt. Implementace [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) udržuje počet odkazů na objekt – objekt není odstraněn, dokud jeho počet odkazů nedosáhne nuly.

[AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [vydání](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) jsou poměrně jasné z hlediska implementace. Toto je triviální implementace:

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

Členská funkce [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) je trochu zajímavější. Není velmi zajímavá, že by měl být objekt, jehož jenom členské funkce jsou [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) – je vhodné říct objektu, aby provedl více věcí, než poskytuje [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . To je místo, kde je funkce [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) užitečná. Umožňuje získat jiné "rozhraní" na stejném objektu. Tato rozhraní jsou obvykle odvozena z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) a přidávají další funkce přidáním nových členských funkcí. Rozhraní COM nikdy nemají členské proměnné deklarované v rozhraní a všechny členské funkce jsou deklarovány jako čistě virtuální. Například

```cpp
class IPrintInterface : public IUnknown
{
public:
    virtual void PrintObject() = 0;
};
```

Chcete-li získat IPrintInterface, pokud máte pouze [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), zavolejte [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pomocí `IID` `IPrintInterface`. `IID` je 128 číslo, které rozhraní jednoznačně identifikuje. Existuje `IID` pro každé rozhraní, které definujete buď vy nebo OLE. Pokud *punk* je ukazatel na objekt [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) , kód, ze kterého se má IPrintInterface načíst, může být:

```cpp
IPrintInterface* pPrint = NULL;
if (pUnk->QueryInterface(IID_IPrintInterface, (void**)&pPrint) == NOERROR)
{
    pPrint->PrintObject();
    pPrint->Release();
    // release pointer obtained via QueryInterface
}
```

To je poměrně snadné, ale jak byste implementovali objekt podporující rozhraní IPrintInterface a [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) v tomto případě je to jednoduché, protože IPrintInterface je odvozen přímo z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) – implementací IPrintInterface, [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) je automaticky podporován. Příklad:

```cpp
class CPrintObj : public CPrintInterface
{
    virtual HRESULT QueryInterface(REFIID iid, void** ppvObj);
    virtual ULONG AddRef();
    virtual ULONG Release();
    virtual void PrintObject();
};
```

Implementace [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) budou přesně stejné jako u implementací uvedených výše. `CPrintObj::QueryInterface` by vypadalo přibližně takto:

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

Jak vidíte, pokud je identifikátor rozhraní (IID) rozpoznán, je vrácen do objektu ukazatel. v opačném případě dojde k chybě. Všimněte si také, že výsledkem úspěchu [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) je implicitní [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref). Samozřejmě byste také museli implementovat CEditObj::P isknout. To je jednoduché, protože IPrintInterface byl přímo odvozen od rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) . Pokud jste však chtěli podporovat dvě různá rozhraní, jak je odvozeno od [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), vezměte v úvahu následující:

```cpp
class IEditInterface : public IUnkown
{
public:
    virtual void EditObject() = 0;
};
```

I když existuje řada různých způsobů, jak implementovat třídu podporující IEditInterface i IPrintInterface, včetně použití C++ vícenásobné dědičnosti, tato poznámka se soustředí na použití vnořených tříd pro implementaci této funkce.

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

Celá implementace je uvedená níže:

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

Všimněte si, že většina implementace [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) je umístěna do třídy CEditPrintObj namísto Duplikace kódu v CEditPrintObj:: CEditObj a CEditPrintObj:: CPrintObj. Tím se sníží množství kódu a vyhne se chybám. Klíčovým bodem, který je tady z rozhraní IUnknown, je možné zavolat funkci [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) , aby se načetlo rozhraní, které může objekt podporovat, a z každého z těchto rozhraní je možné provést stejnou činnost. To znamená, že všechny funkce [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) dostupné z každého rozhraní se musí chovat naprosto stejným způsobem. Aby tyto vložené objekty volaly implementaci v "vnějším objektu", je použit zpětný ukazatel (m_pParent). Ukazatel m_pParent je inicializován během konstruktoru CEditPrintObj. Pak byste implementovali CEditPrintObj:: CPrintObj::P rintObject a CEditPrintObj:: CEditObj:: EditObject i. Byl přidán poměrně nějaký bitový kód pro přidání jedné funkce – možnost upravovat objekt. Naštěstí je poměrně Neběžné, že rozhraní mají pouze jednu členskou funkci (i když k tomu dojde) a v tomto případě by EditObject a PrintObject byly obvykle zkombinovány do jediného rozhraní.

To je velké množství vysvětlení a velké množství kódu pro takový jednoduchý scénář. Třídy MFC/OLE poskytují jednodušší alternativu. Implementace MFC používá techniku podobnou způsobu, jakým jsou zprávy systému Windows zabaleny pomocí map zpráv. Toto zařízení se nazývá *mapy rozhraní* a je popsáno v další části.

## <a name="mfc-interface-maps"></a>Mapy rozhraní MFC

MFC/OLE zahrnuje implementaci "map rozhraní", která se podobá "mapách zpráv v knihovně MFC" Maps "a" Maps "v rámci konceptu a provádění. Základní funkce map rozhraní knihovny MFC jsou následující:

- Standardní implementace rozhraní [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), integrovaná do třídy `CCmdTarget`.

- Údržba počtu odkazů, který změnil [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref) a [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)

- Implementovaná implementace [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) na základě dat

Kromě toho mapy rozhraní podporují tyto rozšířené funkce:

- Podpora pro vytváření agregovatelné objekty COM

- Podpora použití agregačních objektů v implementaci objektu COM

- Implementace je vidlicová a rozšiřitelná.

Další informace o agregaci naleznete v tématu [agregace](/windows/win32/com/aggregation) .

Podpora mapování rozhraní knihovny MFC je zarootovaná ve třídě `CCmdTarget`. `CCmdTarget` "*má*" počet odkazů a všechny členské funkce přidružené k implementaci [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (například počet odkazů je v `CCmdTarget`). Chcete-li vytvořit třídu, která podporuje OLE COM, odvozujete třídu od `CCmdTarget` a použijete různá makra a členské funkce `CCmdTarget` k implementaci požadovaných rozhraní. Implementace knihovny MFC používá vnořené třídy k definování každé implementace rozhraní podobně jako v příkladu výše. To je snazší díky standardní implementaci rozhraní IUnknown a také k množství maker, které eliminují některé opakující kód.

## <a name="interface-map-basics"></a>Základy mapování rozhraní

### <a name="to-implement-a-class-using-mfcs-interface-maps"></a>Implementace třídy pomocí map rozhraní MFC

1. Odvodit třídu buď přímo, nebo nepřímo z `CCmdTarget`.

2. Použijte funkci `DECLARE_INTERFACE_MAP` v definici odvozené třídy.

3. Pro každé rozhraní, které chcete podporovat, použijte makra BEGIN_INTERFACE_PART a END_INTERFACE_PART v definici třídy.

4. V implementačním souboru použijte makra BEGIN_INTERFACE_MAP a END_INTERFACE_MAP k definování mapy rozhraní třídy.

5. Pro každý podporovaný identifikátor IID použijte makro INTERFACE_PART mezi BEGIN_INTERFACE_MAP a END_INTERFACE_MAP makra k mapování tohoto identifikátoru IID na konkrétní "část" vaší třídy.

6. Implementujte všechny vnořené třídy, které reprezentují rozhraní, které podporujete.

7. Použijte makro METHOD_PROLOGUE pro přístup k nadřazenému objektu odvozenému `CCmdTarget`.

8. [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) mohou delegovat na `CCmdTarget` implementaci těchto funkcí (`ExternalAddRef`, `ExternalRelease`a `ExternalQueryInterface`).

Výše uvedený příklad CPrintEditObj může být implementován následujícím způsobem:

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

Výše uvedená deklarace vytvoří třídu odvozenou z `CCmdTarget`. DECLARE_INTERFACE_MAP makro oznamuje rozhraní, že tato třída bude mít vlastní mapu rozhraní. Kromě toho makra BEGIN_INTERFACE_PART a END_INTERFACE_PART definují vnořené třídy, v tomto případě s názvy CEditObj a CPrintObj (X se používá pouze k odlišení vnořených tříd od globálních tříd, které začínají na "C" a tříd rozhraní, které Začněte s "I"). Vytvoří se dva vnořené členy těchto tříd: m_CEditObj a m_CPrintObj, v uvedeném pořadí. Makra automaticky deklarují funkce [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) ; Proto deklarujete pouze funkce, které jsou specifické pro toto rozhraní: EditObject a PrintObject (je použito makro OLE STDMETHOD, aby byly k dispozici **_stdcall** a virtuální klíčová slova jako vhodná pro cílovou platformu).

Pro implementaci mapy rozhraní pro tuto třídu:

```cpp
BEGIN_INTERFACE_MAP(CPrintEditObj, CCmdTarget)
    INTERFACE_PART(CPrintEditObj, IID_IPrintInterface, PrintObj)
    INTERFACE_PART(CPrintEditObj, IID_IEditInterface, EditObj)
END_INTERFACE_MAP()
```

To spojuje IID_IPrintInterface IID pomocí m_CPrintObj a IID_IEditInterface s m_CEditObj. `CCmdTarget` implementace [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) (`CCmdTarget::ExternalQueryInterface`) používá tuto mapu k vrácení ukazatelů na m_CPrintObj a m_CEditObj, pokud je požadováno. Není nutné zahrnout položku pro `IID_IUnknown`; rozhraní použije první rozhraní v mapě (v tomto případě m_CPrintObj), pokud je požadováno `IID_IUnknown`.

I když makro BEGIN_INTERFACE_PART automaticky deklarovalo funkce [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release) a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) pro vás, je stále nutné je implementovat:

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

Implementace pro CEditPrintObj:: CPrintObj bude podobná výše uvedeným definicím pro CEditPrintObj:: CEditObj. I když by bylo možné vytvořit makro, které by bylo možné použít k automatickému generování těchto funkcí (ale dříve v vývoji MFC/OLE), je obtížné nastavit body přerušení, když makro generuje více než jeden řádek kódu. Z tohoto důvodu je tento kód rozbalen ručně.

Pomocí implementace rozhraní map zpráv je k dispozici několik věcí, které není nutné provést:

- Implementace QueryInterface

- Implementace AddRef a Release

- Deklarovat jednu z těchto integrovaných metod na obou vašich rozhraních

Rozhraní navíc používá interní mapování zpráv. To vám umožňuje odvozovat z třídy rozhraní, například `COleServerDoc`, která již podporuje určitá rozhraní a poskytuje buď náhrady nebo doplňky rozhraní poskytovaných rozhraním. To lze provést, protože rozhraní plně podporuje dědění mapování rozhraní ze základní třídy. To je důvod, proč BEGIN_INTERFACE_MAP přebírá jako druhý parametr název základní třídy.

> [!NOTE]
> Obecně není možné znovu použít implementaci předdefinovaných implementací knihovny MFC rozhraní OLE, a to pouze děděním vložené specializace rozhraní z verze knihovny MFC. To není možné, protože použití makra METHOD_PROLOGUE pro získání přístupu k objektu odvozenému `CCmdTarget`implikuje *pevný posun* vloženého objektu z objektu odvozeného z `CCmdTarget`. To znamená, že nemůžete například odvodit vložené Myadvisesink z implementace knihovny MFC v `COleClientItem::XAdviseSink`, protože XAdviseSink spoléhá na konkrétní posun od horní části objektu `COleClientItem`.

> [!NOTE]
> Můžete však delegovat na implementaci knihovny MFC pro všechny funkce, které mají výchozí chování knihovny MFC. To se provádí v implementaci knihovny MFC `IOleInPlaceFrame` (XOleInPlaceFrame) ve třídě `COleFrameHook` (deleguje na m_xOleInPlaceUIWindow pro mnoho funkcí). Tento návrh byl zvolen pro snížení běhové velikosti objektů, které implementují mnoho rozhraní; eliminuje nutnost zpětného ukazatele (například způsobu, jakým se použil m_pParent v předchozí části).

### <a name="aggregation-and-interface-maps"></a>Agregace a mapy rozhraní

Kromě podpory samostatných objektů COM podporuje i knihovna MFC také agregaci. Vlastní agregace je příliš složitá téma, které by bylo možné diskutovat. Další informace o agregaci naleznete v tématu [agregace](/windows/win32/com/aggregation) . Tato Poznámka bude jednoduše popsat podporu agregace integrované do map rozhraní a rozhraní.

Existují dva způsoby použití agregace: (1) použití objektu COM, který podporuje agregaci, a (2) implementace objektu, který lze agregovat jiným. Tyto možnosti se dají označovat jako "použití agregačního objektu" a "vytvoření objektu, který lze agregovat". Knihovna MFC podporuje obojí.

### <a name="using-an-aggregate-object"></a>Použití agregačního objektu

Chcete-li použít agregovaný objekt, musí být nějaký způsob, jak spojit agregaci s mechanismem QueryInterface. Jinými slovy, agregovaný objekt se musí chovat, jako by se jednalo o nativní část vašeho objektu. Takže to, jak to dělá do mechanismu mapování rozhraní knihovny MFC, kromě makra INTERFACE_PART, kde je vnořený objekt mapován na identifikátor IID, můžete také deklarovat agregovaný objekt jako součást vaší `CCmdTarget` odvozené třídy. K tomu je použito makro INTERFACE_AGGREGATE. To umožňuje zadat členskou proměnnou (která musí být ukazatel na třídu [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) nebo odvozenou třídu), která má být integrována do mechanismu mapování rozhraní. Pokud ukazatel nemá hodnotu NULL při volání `CCmdTarget::ExternalQueryInterface`, rozhraní automaticky zavolá členskou funkci [QueryInterface objektu QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) , pokud požadovaný `IID` není jedním z nativních `IID`s podporovaným objektem `CCmdTarget`.

#### <a name="to-use-the-interface_aggregate-macro"></a>Použití makra INTERFACE_AGGREGATE

1. Deklarujete členskou proměnnou (`IUnknown*`), která bude obsahovat ukazatel na agregovaný objekt.

2. Do mapy rozhraní zahrňte INTERFACE_AGGREGATE makro, které odkazuje na členskou proměnnou podle názvu.

3. V určitém okamžiku (obvykle během `CCmdTarget::OnCreateAggregates`) inicializujte členskou proměnnou na jinou hodnotu než NULL.

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

Proměnná m_lpAggrInner byla inicializována v konstruktoru na hodnotu NULL. Rozhraní ignoruje členskou proměnnou NULL ve výchozí implementaci [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). `OnCreateAggregates` je vhodné místo pro vytvoření vašich agregačních objektů. Budete je muset volat explicitně, pokud vytváříte objekt mimo implementaci knihovny MFC `COleObjectFactory`. Důvodem pro vytváření agregovaných hodnot v `CCmdTarget::OnCreateAggregates` a použití `CCmdTarget::GetControllingUnknown` se při vytváření agregovaných objektů objeví zjevné.

Tato technika poskytne vašemu objektu všechna rozhraní, která podporuje agregovaný objekt, a jeho nativní rozhraní. Pokud chcete pouze podmnožinu rozhraní, která podporuje agregace, můžete přepsat `CCmdTarget::GetInterfaceHook`. To vám umožní hodně se zahnutí na nízké úrovni, podobně jako [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)). Obvykle požadujete všechna rozhraní, která agregace podporuje.

### <a name="making-an-object-implementation-aggregatable"></a>Vytvoření agregovatelné implementace objektu

Pro agregaci objektu musí implementace [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) delegovat na "řízení neznámé". Jinými slovy, aby mohl být součástí objektu, musí delegovat [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) na jiný objekt, také odvozený z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Tato "řídicí neznámá" je při vytvoření objektu k dispozici, to znamená, že je k dispozici pro implementaci `COleObjectFactory`. Implementace těchto prostředků přináší menší množství režie a v některých případech není žádoucí, takže knihovna MFC tuto volitelnou. Chcete-li povolit agregaci objektu, zavolejte `CCmdTarget::EnableAggregation` z konstruktoru objektu.

Pokud objekt také používá agregace, je nutné také předat správné "řízení neznámé" do agregovaných objektů. Tento ukazatel [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) je obvykle předán objektu při vytvoření agregace. Například Parametr pUnkOuter je "řízení neznámé" pro objekty vytvořené pomocí `CoCreateInstance`. Správný ukazatel "řízení neznámá" lze načíst voláním `CCmdTarget::GetControllingUnknown`. Hodnota vrácená z této funkce však není během konstruktoru platná. Z tohoto důvodu je doporučeno vytvořit agregace pouze v přepsání `CCmdTarget::OnCreateAggregates`, kde návratová hodnota z `GetControllingUnknown` je spolehlivá, i když je vytvořena z implementace `COleObjectFactory`.

Je také důležité, aby objekt při přidávání nebo uvolňování umělých odkazů spolupracuje se správným počtem odkazů. Chcete-li se ujistit, že se jedná o tento případ, vždy zavolejte `ExternalAddRef` a `ExternalRelease` namísto `InternalRelease` a `InternalAddRef`. Je málo pravděpodobné volat `InternalRelease` nebo `InternalAddRef` na třídu, která podporuje agregaci.

## <a name="reference-material"></a>Referenční materiál

Pokročilé použití technologie OLE, jako je definování vlastních rozhraní nebo přepsání implementace rozhraní OLE, vyžaduje použití základního mechanismu mapování rozhraní.

V této části jsou popsána jednotlivá makra a rozhraní API, která slouží k implementaci těchto pokročilých funkcí.

### <a name="ccmdtargetenableaggregation--function-description"></a>CCmdTarget:: EnableAggregation – Popis funkce

```cpp
void EnableAggregation();
```

#### <a name="remarks"></a>Poznámky

Voláním této funkce v konstruktoru odvozené třídy, pokud chcete podporovat agregaci OLE pro objekty tohoto typu. Tím se připraví speciální implementace IUnknown, která je nutná pro agregovatelné objekty.

### <a name="ccmdtargetexternalqueryinterface--function-description"></a>CCmdTarget:: ExternalQueryInterface – Popis funkce

```cpp
DWORD ExternalQueryInterface(
    const void FAR* lpIID,
    LPVOIDFAR* ppvObj
);
```

#### <a name="parameters"></a>Parametry

*lpIID*<br/>
Zcela ukazatel na IID (první argument pro QueryInterface)

*ppvObj*<br/>
Ukazatel na IUnknown * (druhý argument na QueryInterface)

#### <a name="remarks"></a>Poznámky

Zavolejte tuto funkci v implementaci IUnknown pro každé rozhraní, které vaše třída implementuje. Tato funkce poskytuje standardní datově řízenou implementaci QueryInterface na základě mapy rozhraní vašeho objektu. Je nutné přetypovat návratovou hodnotu na HRESULT. Pokud je objekt agregovaný, tato funkce místo použití mapování místních rozhraní zavolá "řízení IUnknown".

### <a name="ccmdtargetexternaladdref--function-description"></a>CCmdTarget:: ExternalAddRef – Popis funkce

```cpp
DWORD ExternalAddRef();
```

#### <a name="remarks"></a>Poznámky

Zavolejte tuto funkci v implementaci IUnknown:: AddRef pro každé rozhraní, které vaše třída implementuje. Vrácená hodnota je nový počet odkazů na objekt CCmdTarget. Pokud objekt je agregován, tato funkce bude volat "řízení IUnknown" namísto manipulace s místním počtem odkazů.

### <a name="ccmdtargetexternalrelease--function-description"></a>CCmdTarget:: ExternalRelease – Popis funkce

```cpp
DWORD ExternalRelease();
```

#### <a name="remarks"></a>Poznámky

Zavolejte tuto funkci v implementaci IUnknown:: Release pro každé rozhraní, které vaše třída implementuje. Vrácená hodnota označuje nový počet odkazů na objekt. Pokud objekt je agregován, tato funkce bude volat "řízení IUnknown" namísto manipulace s místním počtem odkazů.

### <a name="declare_interface_map--macro-description"></a>DECLARE_INTERFACE_MAP – popis makra

```cpp
DECLARE_INTERFACE_MAP
```

#### <a name="remarks"></a>Poznámky

Toto makro použijte v jakékoli třídě odvozené z `CCmdTarget`, která bude mít mapu rozhraní. Používá se podobným způsobem jako DECLARE_MESSAGE_MAP. Vyvolání makra by mělo být umístěno v definici třídy, obvykle v hlavičce (. H) souboru. Třída s DECLARE_INTERFACE_MAP musí definovat mapu rozhraní v implementačním souboru (. CPP) pomocí makra BEGIN_INTERFACE_MAP a END_INTERFACE_MAP.

### <a name="begin_interface_part-and-end_interface_part--macro-descriptions"></a>BEGIN_INTERFACE_PART a END_INTERFACE_PART – popisy maker

```cpp
BEGIN_INTERFACE_PART(localClass, iface);
END_INTERFACE_PART(localClass)
```

#### <a name="parameters"></a>Parametry

*localClass*<br/>
Název třídy, která implementuje rozhraní

*iface*<br/>
Název rozhraní, které tato třída implementuje

#### <a name="remarks"></a>Poznámky

Pro každé rozhraní, které vaše třída implementuje, je nutné mít dvojici BEGIN_INTERFACE_PART a END_INTERFACE_PART. Tato makra definují místní třídu odvozenou z rozhraní OLE, které definujete, a také vloženou členskou proměnnou této třídy. Členy [AddRef](/windows/win32/api/unknwn/nf-unknwn-iunknown-addref), [release](/windows/win32/api/unknwn/nf-unknwn-iunknown-release)a [QueryInterface](/windows/win32/api/unknwn/nf-unknwn-iunknown-queryinterface(q)) jsou deklarovány automaticky. Je nutné zahrnout deklarace pro ostatní členské funkce, které jsou součástí implementovaného rozhraní (tyto deklarace jsou umístěny mezi BEGIN_INTERFACE_PART a END_INTERFACE_PART makra).

Argument *iface* je rozhraní OLE, které chcete implementovat, například `IAdviseSink`nebo `IPersistStorage` (nebo vlastní rozhraní).

Argument *localClass* je název místní třídy, která bude definována. K názvu se automaticky přidá znak "X". Tato konvence pojmenování se používá k zamezení kolizí s globálními třídami se stejným názvem. Kromě toho název vloženého člena je stejný jako název *localClass* s výjimkou, že je předpona ' m_x '.

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

by definovali místní třídu s názvem Myadvisesink odvozenou z IAdviseSink a člena třídy, ve které je deklarována s názvem m_xMyAdviseSink. Poznámka:

> [!NOTE]
> Řádky začínající na `STDMETHOD`_ jsou v podstatě zkopírovány z OLE2. H a mírně se změnily. Kopírují se z OLE2. H může snížit chyby, které je obtížné vyřešit.

### <a name="begin_interface_map-and-end_interface_map--macro-descriptions"></a>BEGIN_INTERFACE_MAP a END_INTERFACE_MAP – popisy maker

```cpp
BEGIN_INTERFACE_MAP(theClass, baseClass)
END_INTERFACE_MAP
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Třída, ve které má být definována mapa rozhraní

*baseClass*<br/>
Třída, ze které je odvozeno *theclass* .

#### <a name="remarks"></a>Poznámky

Makra BEGIN_INTERFACE_MAP a END_INTERFACE_MAP se v implementačním souboru používají ke skutečnému definování mapy rozhraní. Pro každé rozhraní, které je implementováno, je jedno nebo více INTERFACE_PART volání makra. Pro každou agregaci, kterou třída používá, je k dispozici jedno INTERFACE_AGGREGATE vyvolání makra.

### <a name="interface_part--macro-description"></a>INTERFACE_PART – popis makra

```cpp
INTERFACE_PART(theClass, iid, localClass)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy, která obsahuje mapu rozhraní.

*iid*<br/>
`IID`, která má být namapována na vloženou třídu.

*localClass*<br/>
Název místní třídy (minus znak "X").

#### <a name="remarks"></a>Poznámky

Toto makro se používá mezi BEGIN_INTERFACE_MAP makro a END_INTERFACE_MAP makro pro každé rozhraní, které bude váš objekt podporovat. Umožňuje mapovat IID na člena třídy označené *theclass* a *localClass*. M_x se automaticky přidá do *localClass* . Všimněte si, že k jednomu členovi může být přidruženo více než jeden `IID`. To je velmi užitečné, Pokud implementujete pouze "největší odvozené" rozhraní a chcete zajistit také všechna Pokročilá rozhraní. Dobrým příkladem je `IOleInPlaceFrameWindow` rozhraní. Jeho hierarchie vypadá takto:

```Hierarchy
IUnknown
    IOleWindow
        IOleUIWindow
            IOleInPlaceFrameWindow
```

Pokud objekt implementuje `IOleInPlaceFrameWindow`, může klient `QueryInterface` na kterékoli z těchto rozhraní: `IOleUIWindow`, `IOleWindow`nebo [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown), kromě "nejvíce odvozeného" rozhraní `IOleInPlaceFrameWindow` (ten, který skutečně implementujete). K tomu můžete použít více než jedno INTERFACE_PART makro k namapování každého základního rozhraní na `IOleInPlaceFrameWindow` rozhraní:

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

Rozhraní IUnknown má za starosti, protože je vždy vyžadováno.

### <a name="interface_part--macro-description"></a>INTERFACE_PART – popis makra

```cpp
INTERFACE_AGGREGATE(theClass, theAggr)
```

#### <a name="parameters"></a>Parametry

*theClass*<br/>
Název třídy, která obsahuje mapu rozhraní,

*theAggr*<br/>
Název členské proměnné, která se má agregovat.

#### <a name="remarks"></a>Poznámky

Toto makro slouží k oznámení rozhraní, že třída používá agregovaný objekt. Musí se objevit mezi BEGIN_INTERFACE_PART a END_INTERFACE_PART makra. Agregovaný objekt je samostatný objekt odvozený z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown). Pomocí agregace a INTERFACE_AGGREGATE makra můžete učinit všechna rozhraní, která agregace podporuje, aby byla přímo podporována objektem. Argument *theAggr* je jednoduchý název členské proměnné vaší třídy, která je odvozena z [IUnknown](/windows/win32/api/unknwn/nn-unknwn-iunknown) (buď přímo nebo nepřímo). Všechna INTERFACE_AGGREGATEová makra musí při umístění na mapě rozhraní splňovat INTERFACE_PART makra.

## <a name="see-also"></a>Viz také:

[Technické poznámky podle čísel](../mfc/technical-notes-by-number.md)<br/>
[Technické poznámky podle kategorií](../mfc/technical-notes-by-category.md)
