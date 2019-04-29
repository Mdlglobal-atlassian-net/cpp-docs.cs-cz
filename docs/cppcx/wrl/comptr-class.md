---
title: ComPtr – třída
ms.date: 10/01/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::ComPtr
- client/Microsoft::WRL::ComPtr::As
- client/Microsoft::WRL::ComPtr::AsIID
- client/Microsoft::WRL::ComPtr::AsWeak
- client/Microsoft::WRL::ComPtr::Attach
- client/Microsoft::WRL::ComPtr::ComPtr
- client/Microsoft::WRL::ComPtr::CopyTo
- client/Microsoft::WRL::ComPtr::Detach
- client/Microsoft::WRL::ComPtr::Get
- client/Microsoft::WRL::ComPtr::GetAddressOf
- client/Microsoft::WRL::ComPtr::InternalAddRef
- client/Microsoft::WRL::ComPtr::InternalRelease
- client/Microsoft::WRL::ComPtr::operator&
- client/Microsoft::WRL::ComPtr::operator->
- client/Microsoft::WRL::ComPtr::operator=
- client/Microsoft::WRL::ComPtr::operator==
- client/Microsoft::WRL::ComPtr::operator!=
- client/Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType
- client/Microsoft::WRL::ComPtr::ptr_
- client/Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf
- client/Microsoft::WRL::ComPtr::Reset
- client/Microsoft::WRL::ComPtr::Swap
- client/Microsoft::WRL::ComPtr::~ComPtr
helpviewer_keywords:
- Microsoft::WRL::ComPtr class
- Microsoft::WRL::ComPtr::As method
- Microsoft::WRL::ComPtr::AsIID method
- Microsoft::WRL::ComPtr::AsWeak method
- Microsoft::WRL::ComPtr::Attach method
- Microsoft::WRL::ComPtr::ComPtr, constructor
- Microsoft::WRL::ComPtr::CopyTo method
- Microsoft::WRL::ComPtr::Detach method
- Microsoft::WRL::ComPtr::Get method
- Microsoft::WRL::ComPtr::GetAddressOf method
- Microsoft::WRL::ComPtr::InternalAddRef method
- Microsoft::WRL::ComPtr::InternalRelease method
- Microsoft::WRL::ComPtr::operator& operator
- Microsoft::WRL::ComPtr::operator-> operator
- Microsoft::WRL::ComPtr::operator= operator
- Microsoft::WRL::ComPtr::operator== operator
- Microsoft::WRL::ComPtr::operator!= operator
- Microsoft::WRL::ComPtr::operator Microsoft::WRL::Details::BoolType operator
- Microsoft::WRL::ComPtr::ptr_ data member
- Microsoft::WRL::ComPtr::ReleaseAndGetAddressOf method
- Microsoft::WRL::ComPtr::Reset method
- Microsoft::WRL::ComPtr::Swap method
- Microsoft::WRL::ComPtr::~ComPtr, destructor
ms.assetid: a6551902-6819-478a-8df7-b6f312ab1fb0
ms.openlocfilehash: 9e5b2419f070ead17e72b1642f510f74bad8260e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62398677"
---
# <a name="comptr-class"></a>ComPtr – třída

Vytvoří *inteligentního ukazatele* typ, který představuje rozhraní určené typem parametru šablony. `ComPtr` automaticky udržuje počet odkazů pro základního ukazatele rozhraní a uvolní rozhraní, když počet odkazů dosáhne nuly.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Rozhraní, která `ComPtr` představuje.

*U*<br/>
Třída, ke kterému aktuální `ComPtr` je friend. (Šablona, která používá tento parametr je chráněna.)

## <a name="remarks"></a>Poznámky

`ComPtr<>` deklaruje typ, který představuje základního ukazatele rozhraní. Použít `ComPtr<>` deklarovat proměnnou a pak použijte šipku operátora přístupu členů (`->`) pro přístup k členská funkce rozhraní.

Další informace o inteligentních ukazatelích naleznete v tématu "Chytrých ukazatelů COM" dílčí část objektu [postupy kódování COM](/windows/desktop/LearnWin32/com-coding-practices) v knihovně MSDN.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice TypeDef

Název            | Popis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonymum pro typ zadaný *T* parametr šablony.

### <a name="public-constructors"></a>Veřejné konstruktory

Název                             | Popis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[Comptr::comptr –](#comptr)        | Inicializuje novou instanci třídy `ComPtr` třídy. Přetížení poskytují výchozí, kopírovat, přesunout a převod konstruktory.
[ComPtr::~ComPtr](#tilde-comptr) | Uvolní instanci `ComPtr`.

### <a name="public-methods"></a>Veřejné metody

Název                                                      | Popis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[Comptr::AS –](#as)                                         | Vrátí `ComPtr` objekt, který představuje rozhraní identifikován parametrem určené šablony.
[ComPtr::AsIID](#asiid)                                   | Vrátí `ComPtr` objekt, který představuje rozhraní, které identifikují pomocí ID zadané rozhraní.
[Comptr::asweak –](#asweak)                                 | Získá nestálý odkaz na aktuální objekt.
[ComPtr::Attach](#attach)                                 | Přidruží to `ComPtr` s typem rozhraní určeném aktuálním parametru typu šablony.
[ComPtr::CopyTo](#copyto)                                 | Zkopíruje aktuální nebo zadané rozhraní přidružené k tomuto `ComPtr` na ukazatel zadaným výstupem.
[ComPtr::Detach](#detach)                                 | Zruší přidružení to `ComPtr` z rozhraní, které představuje.
[Comptr::Get –](#get)                                       | Načte ukazatel rozhraní, které souvisí s tímto `ComPtr`.
[ComPtr::GetAddressOf](#getaddressof)                     | Načte adresu [ptr_ –](#ptr) datový člen, který obsahuje ukazatel na rozhraní představovaného tímto rozhraním `ComPtr`.
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Uvolní rozhraní přidružené k tomuto `ComPtr` a potom načte adresu [ptr_ –](#ptr) datový člen, který obsahuje ukazatel rozhraní, která byla vydána.
[ComPtr::Reset](#reset)                                   | Uvolní všechny odkazy pro ukazatele na rozhraní, které souvisí s tímto `ComPtr`.
[Comptr::swap –](#swap)                                     | Vymění rozhraní spravuje aktuální `ComPtr` rozhraní spravuje zadaný `ComPtr`.

### <a name="protected-methods"></a>Chráněné metody

Název                                        | Popis
------------------------------------------- | --------------------------------------------------------------------------------
[Comptr::internaladdref –](#internaladdref)   | Zvýší počet odkazů přidružený k tomuto rozhraní `ComPtr`.
[Comptr::internalrelease –](#internalrelease) | Provádí operaci vydání COM pro rozhraní přidružené k tomuto `ComPtr`.

### <a name="public-operators"></a>Veřejné operátory

Název                                                                                           | Popis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::operator &](#operator-ampersand)                                                       | Načte adresu aktuálního `ComPtr`.
[ComPtr::operator->](#operator-arrow)                                                          | Načte ukazatel na typ určený v parametru aktuální šablony.
[ComPtr::operator =](#operator-assign)                                                          | Přiřadí hodnotu k aktuální `ComPtr`.
[ComPtr::operator ==](#operator-equality)                                                       | Určuje, zda dva `ComPtr` objekty rovnají.
[ComPtr::operator! =](#operator-inequality)                                                     | Určuje, zda dva `ComPtr` objekty nejsou stejné.
[ComPtr::operator Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Určuje, zda je či není `ComPtr` spravuje doba života objektu rozhraní.

### <a name="protected-data-members"></a>Chránění členové dat

Název                 | Popis
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::ptr_](#ptr) | Obsahuje ukazatel rozhraní, který je přidružený k a spravovaného touto `ComPtr`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="tilde-comptr"></a>ComPtr::~ComPtr

Uvolní instanci `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>Comptr::AS –

Vrátí `ComPtr` objekt, který představuje rozhraní identifikován parametrem určené šablony.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* p
) const;

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> p
) const;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Rozhraní a nelze je reprezentovat podle parametrů *p*.

*p*<br/>
A `ComPtr` objekt, který představuje rozhraní určené typem parametru *U*. Parametr *p* nesmí odkazovat na aktuální `ComPtr` objektu.

### <a name="remarks"></a>Poznámky

První šablona je formulář, který by měl používat ve vašem kódu. Druhá šablona se osobní a specializace pomocné rutiny, podporující funkcí jazyka C++, jako [automaticky](../../cpp/auto-cpp.md) klíčovým slovem odvození typu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="asiid"></a>ComPtr::AsIID

Vrátí `ComPtr` objekt, který představuje rozhraní, které identifikují pomocí ID zadané rozhraní.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*p*<br/>
Pokud objekt má rozhraní, jejichž ID se rovná *riid*, dvakrát nepřímé ukazatel na rozhraní určené typem *riid* parametr; jinak vrátí hodnotu, ukazatel na `IUnknown`.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="asweak"></a>Comptr::asweak –

Získá nestálý odkaz na aktuální objekt.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parametry

*pWeakRef*<br/>
Když tato operace dokončí, ukazatel na objekt nestálý odkaz.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, která označuje chybu.

## <a name="attach"></a>ComPtr::Attach

Přidruží to `ComPtr` s typem rozhraní určeném aktuálním parametru typu šablony.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*Ostatní*<br/>
Typ rozhraní.

## <a name="comptr"></a>Comptr::comptr –

Inicializuje novou instanci třídy `ComPtr` třídy. Přetížení poskytují výchozí, kopírovat, přesunout a převod konstruktory.

```cpp
WRL_NOTHROW ComPtr();
WRL_NOTHROW ComPtr(
   decltype(__nullptr)
);
template<class U>
WRL_NOTHROW ComPtr(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr(
   const ComPtr& other
);
template<class U>
WRL_NOTHROW ComPtr(
   const ComPtr<U> &other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other,
   typename ENABLE_IF<__is_convertible_to(U*,
   T*),
   void *>;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Typ *jiných* parametru.

*Ostatní*<br/>
Objekt typu *U*.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

První konstruktor je výchozí konstruktor, který vkládacím vytvoří prázdný objekt. Druhý konstruktor Určuje [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), které explicitně vytvoří prázdný objekt.

Třetí konstruktor vytvoří objekt v objektu určeném ukazatel.

Čtvrtý a pátý konstruktor je kopírovací konstruktory. Pátý konstruktor zkopíruje objekt je převést na typ aktuální.

Šestý a sedmý konstruktor jsou konstruktorů. Sedmý konstruktor přesune objekt je převést na typ aktuální.

## <a name="copyto"></a>Comptr::CopyTo –

Zkopíruje aktuální nebo zadané rozhraní přidružené k tomuto `ComPtr` na zadaný ukazatel.

```cpp
HRESULT CopyTo(
   _Deref_out_ InterfaceType** ptr
);

HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ void** ptr
) const;

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
) const;
```

### <a name="parameters"></a>Parametry

*U*<br/>
Název typu.

*ptr*<br/>
Pokud tato operace dokončí, ukazatel na požadované rozhraní.

*riid*<br/>
Identifikátor rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT, který označuje důvod, proč implicitní `QueryInterface` operace se nezdařila.

### <a name="remarks"></a>Poznámky

První funkce vrátí kopii objektu ukazatele na rozhraní přidružené k tomuto `ComPtr`. Tato funkce vždy vrátí hodnotu S_OK.

Druhá funkce provádí `QueryInterface` operace v rozhraní přidružené k tomuto `ComPtr` pro rozhraní určené typem *riid* parametru.

Třetí funkce provádí `QueryInterface` operace v rozhraní přidružené k tomuto `ComPtr` základního rozhraní *U* parametru.

## <a name="detach"></a>ComPtr::Detach

Zruší přidružení to `ComPtr` objekt z rozhraní, které představuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní, která je reprezentována to `ComPtr` objektu.

## <a name="get"></a>Comptr::Get –

Načte ukazatel rozhraní, které souvisí s tímto `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel rozhraní, která souvisí s tímto `ComPtr`.

## <a name="getaddressof"></a>ComPtr::GetAddressOf

Načte adresu [ptr_ –](#ptr) datový člen, který obsahuje ukazatel na rozhraní představovaného tímto rozhraním `ComPtr`.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Adresa proměnné.

## <a name="internaladdref"></a>Comptr::internaladdref –

Zvýší počet odkazů přidružený k tomuto rozhraní `ComPtr`.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Poznámky

Tato metoda je chráněna.

## <a name="internalrelease"></a>Comptr::internalrelease –

Provádí operaci vydání COM pro rozhraní přidružené k tomuto `ComPtr`.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Poznámky

Tato metoda je chráněna.

## <a name="operator-ampersand"></a>ComPtr::operator&amp;

Uvolní rozhraní přidružené k tomuto `ComPtr` objekt a potom načte adresu `ComPtr` objektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Návratová hodnota

Slabý odkaz na aktuální `ComPtr`.

### <a name="remarks"></a>Poznámky

Tato metoda se liší od [comptr::getaddressof –](#getaddressof) v tom, že tato metoda uvolní odkaz na ukazatel rozhraní. Použití `ComPtr::GetAddressOf` když vyžadovat adresy ukazatel rozhraní, ale nechcete, aby k uvolnění rozhraní.

## <a name="operator-arrow"></a>ComPtr::operator-&gt;

Načte ukazatel na typ určený v parametru aktuální šablony.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na typ určený aktuální typ název šablony.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce odebere zbytečnou režii způsobena použitím STDMETHOD – makro. Díky této funkci `IUnknown` typy `private` místo `virtual`.

## <a name="operator-assign"></a>ComPtr::operator =

Přiřadí hodnotu k aktuální `ComPtr`.

```cpp
WRL_NOTHROW ComPtr& operator=(
   decltype(__nullptr)
);
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ T *other
);
template <typename U>
WRL_NOTHROW ComPtr& operator=(
   _In_opt_ U *other
);
WRL_NOTHROW ComPtr& operator=(
   const ComPtr &other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   const ComPtr<U>& other
);
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr &&other
);
template<class U>
WRL_NOTHROW ComPtr& operator=(
   _Inout_ ComPtr<U>&& other
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Třída.

*Ostatní*<br/>
Ukazatel, odkaz nebo odkaz rvalue na typ nebo jiný `ComPtr`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `ComPtr`.

### <a name="remarks"></a>Poznámky

První verze tohoto operátoru přiřadí aktuální prázdnou hodnotu `ComPtr`.

V druhém verzi, pokud přiřazení ukazatel rozhraní není stejný jako aktuální `ComPtr` ukazatel rozhraní, je druhý ukazatel rozhraní je přiřazen k aktuální `ComPtr`.

Ve třetí verzi je přiřazení ukazatel rozhraní přiřazená aktuální `ComPtr`.

Ve čtvrtém verzi, pokud ukazatel rozhraní přiřazování hodnot není stejný jako aktuální `ComPtr` ukazatel rozhraní, je druhý ukazatel rozhraní je přiřazen k aktuální `ComPtr`.

Je pátá verze kopírovacího operátoru; odkaz na `ComPtr` je přiřazen k aktuální `ComPtr`.

Šestá verze je operátor kopie, která používá přesunutí sémantiky; Odkaz rvalue na `ComPtr` Pokud libovolného typu je statické přetypování a posléze přiřazeny k aktuální `ComPtr`.

Sedmý verze je operátor kopie, která používá přesunutí sémantiky; Odkaz rvalue na `ComPtr` typu *U* je statické přetypování pak a přiřazeny k aktuální `ComPtr`.

## <a name="operator-equality"></a>ComPtr::operator ==

Určuje, zda dva `ComPtr` objekty rovnají.

```cpp
bool operator==(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator==(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator==(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parametry

*a*<br/>
Odkaz na `ComPtr` objektu.

*b*<br/>
Odkaz na jiný `ComPtr` objektu.

### <a name="return-value"></a>Návratová hodnota

První operátor výnosy `true` Pokud objekt *a* rovná objektu *b*; v opačném případě `false`.

Druhý a třetí operátory yield `true` Pokud objekt *a* rovná `nullptr`; v opačném případě `false`.

## <a name="operator-inequality"></a>ComPtr::operator! =

Určuje, zda dva `ComPtr` objekty nejsou stejné.

```cpp
bool operator!=(
   const ComPtr<T>& a,
   const ComPtr<U>& b
);

bool operator!=(
   const ComPtr<T>& a,
   decltype(__nullptr)
);

bool operator!=(
   decltype(__nullptr),
   const ComPtr<T>& a
);
```

### <a name="parameters"></a>Parametry

*a*<br/>
Odkaz na `ComPtr` objektu.

*b*<br/>
Odkaz na jiný `ComPtr` objektu.

### <a name="return-value"></a>Návratová hodnota

První operátor výnosy `true` Pokud objekt *a* není roven objektu *b*; v opačném případě `false`.

Druhý a třetí operátory yield `true` Pokud objekt *a* není roven `nullptr`; v opačném případě `false`.

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::operator Microsoft::WRL::Details::BoolType

Určuje, zda je či není `ComPtr` spravuje doba života objektu rozhraní.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je přidruženo toto rozhraní `ComPtr`, adresu [boolstruct::Member –](boolstruct-structure.md#member) datový člen; v opačném případě `nullptr`.

## <a name="ptr"></a>Comptr::ptr_ –

Obsahuje ukazatel rozhraní, který je přidružený k a spravovaného touto `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Poznámky

`ptr_` je členem interní, chráněná data.

## <a name="releaseandgetaddressof"></a>Comptr::releaseandgetaddressof –

Uvolní rozhraní přidružené k tomuto `ComPtr` a potom načte adresu [ptr_ –](#ptr) datový člen, který obsahuje ukazatel rozhraní, která byla vydána.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Adresa [ptr_ –](#ptr) datový člen tohoto `ComPtr`.

## <a name="reset"></a>ComPtr::Reset

Uvolní všechny odkazy pro ukazatele na rozhraní, které souvisí s tímto `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Návratová hodnota

Počet odkazů vydání, pokud existuje.

## <a name="swap"></a>Comptr::swap –

Vymění rozhraní spravuje aktuální `ComPtr` rozhraní spravuje zadaný `ComPtr`.

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parametry

*r*<br/>
A `ComPtr`.

