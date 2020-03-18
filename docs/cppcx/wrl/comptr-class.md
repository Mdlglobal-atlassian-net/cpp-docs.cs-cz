---
title: ComPtr – třída
ms.date: 07/26/2019
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
ms.openlocfilehash: 1e20a991c8f32027aeea6a17df0534aa6e1c2c43
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2020
ms.locfileid: "79418319"
---
# <a name="comptr-class"></a>ComPtr – třída

Vytvoří typ *inteligentního ukazatele* , který představuje rozhraní určené parametrem šablony. `ComPtr` automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, když počet odkazů překročí nulu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parametry

*Š*<br/>
Rozhraní, které `ComPtr` představuje.

*H*<br/>
Třída, na kterou je aktuální `ComPtr` přítel. (Šablona, která používá tento parametr je chráněná.)

## <a name="remarks"></a>Poznámky

`ComPtr<>` deklaruje typ, který reprezentuje ukazatel základního rozhraní. Použijte `ComPtr<>` k deklaraci proměnné a pak použijte operátor přístupu členů (`->`) k přístupu k členské funkci rozhraní.

Další informace o inteligentních ukazatelích naleznete v pododdílu inteligentních ukazatelů COM v tématu [postupy psaní kódu modelu COM](/windows/win32/LearnWin32/com-coding-practices) v knihovně MSDN.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

Název            | Popis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonymum pro typ určený parametrem šablony *T* .

### <a name="public-constructors"></a>Veřejné konstruktory

Název                             | Popis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr:: ComPtr](#comptr)        | Inicializuje novou instanci třídy `ComPtr`. Přetížení poskytují konstruktory Default, Copy, Move a Conversion.
[ComPtr:: ~ ComPtr](#tilde-comptr) | Zruší inicializaci instance `ComPtr`.

### <a name="public-methods"></a>Veřejné metody

Název                                                      | Popis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: as](#as)                                         | Vrátí objekt `ComPtr`, který představuje rozhraní identifikované zadaným parametrem šablony.
[ComPtr:: AsIID –](#asiid)                                   | Vrátí objekt `ComPtr`, který představuje rozhraní identifikované zadaným ID rozhraní.
[ComPtr:: AsWeak –](#asweak)                                 | Načte slabý odkaz na aktuální objekt.
[ComPtr:: Attach](#attach)                                 | Přidruží tuto `ComPtr` k typu rozhraní určenému parametrem aktuálního typu šablony.
[ComPtr:: CopyTo](#copyto)                                 | Zkopíruje aktuální nebo zadané rozhraní přidružené k tomuto `ComPtr` k zadanému výstupnímu ukazateli.
[ComPtr::D etach](#detach)                                 | Zruší přidružení tohoto `ComPtr` k rozhraní, které představuje.
[ComPtr:: Get](#get)                                       | Načte ukazatel na rozhraní, které je přidruženo k tomuto `ComPtr`.
[ComPtr:: GetAddressOf –](#getaddressof)                     | Načte adresu datového členu [ptr_](#ptr) , který obsahuje ukazatel na rozhraní reprezentované tímto `ComPtr`.
[ComPtr:: Releaseandgetaddressof –](#releaseandgetaddressof) | Uvolní rozhraní přidružené k tomuto `ComPtr` a potom načte adresu datového členu [ptr_](#ptr) , který obsahuje ukazatel na rozhraní, které bylo vydány.
[ComPtr::Reset](#reset)                                   | Uvolní všechny odkazy pro ukazatel na rozhraní, které je přidruženo k tomuto `ComPtr`.
[ComPtr:: swap](#swap)                                     | Vyměňuje rozhraní spravované aktuální `ComPtr` s rozhraním spravovaným zadanou `ComPtr`.

### <a name="protected-methods"></a>Chráněné metody

Název                                        | Popis
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr:: InternalAddRef –](#internaladdref)   | Zvýší počet odkazů rozhraní přidruženého k tomuto `ComPtr`.
[ComPtr:: InternalRelease –](#internalrelease) | Provede operaci uvolnění modelu COM na rozhraní, které je přidruženo k tomuto `ComPtr`.

### <a name="public-operators"></a>Veřejné operátory

Název                                                                                           | Popis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator &](#operator-ampersand)                                                       | Načte adresu aktuálního `ComPtr`.
[ComPtr:: operator->](#operator-arrow)                                                          | Načte ukazatel na typ určený aktuálním parametrem šablony.
[ComPtr:: operator =](#operator-assign)                                                          | Přiřadí hodnotu aktuálnímu `ComPtr`.
[ComPtr:: operator = = – operátor](#operator-equality)                                                       | Určuje, zda jsou dva objekty `ComPtr` stejné.
[ComPtr:: operator! =](#operator-inequality)                                                     | Určuje, zda se dva objekty `ComPtr` neshodují.
[ComPtr:: operator Microsoft:: WRL::D etails:: BoolType –](#operator-microsoft-wrl-details-booltype) | Označuje, zda `ComPtr` Správa životnosti objektu rozhraní.

### <a name="protected-data-members"></a>Chránění členové dat

Název                 | Popis
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::p tr_](#ptr) | Obsahuje ukazatel na rozhraní, které je přidruženo a spravováno tímto `ComPtr`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Obor názvů:** Microsoft:: WRL

## <a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

Zruší inicializaci instance `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr:: as

Vrátí objekt `ComPtr`, který představuje rozhraní identifikované zadaným parametrem šablony.

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

*H*<br/>
Rozhraní, které má být reprezentované parametrem *p*.

*trub*<br/>
Objekt `ComPtr`, který představuje rozhraní určené parametrem *U*. Parametr *p* nesmí odkazovat na aktuální objekt `ComPtr`.

### <a name="remarks"></a>Poznámky

První šablonou je formulář, který byste měli použít ve svém kódu. Druhá šablona je interní podpůrná specializace, která podporuje C++ jazykové funkce, jako je klíčové slovo pro snížení počtu [automatických](../../cpp/auto-cpp.md) typů.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="asiid"></a>ComPtr:: AsIID –

Vrátí objekt `ComPtr`, který představuje rozhraní identifikované zadaným ID rozhraní.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*riid*<br/>
ID rozhraní.

*trub*<br/>
Pokud má objekt rozhraní, jehož ID je rovno *riid*, dvakrát nepřímý ukazatel na rozhraní určené parametrem *riid* ; v opačném případě ukazatel na `IUnknown`.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="asweak"></a>ComPtr:: AsWeak –

Načte slabý odkaz na aktuální objekt.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parametry

*pWeakRef*<br/>
Po dokončení této operace se zobrazí ukazatel na slabý odkazový objekt.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="attach"></a>ComPtr:: Attach

Přidruží tuto `ComPtr` k typu rozhraní určenému parametrem aktuálního typu šablony.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Typ rozhraní.

## <a name="comptr"></a>ComPtr:: ComPtr

Inicializuje novou instanci třídy `ComPtr`. Přetížení poskytují konstruktory Default, Copy, Move a Conversion.

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
   typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);

WRL_NOTHROW ComPtr(
   _Inout_ ComPtr &&other
);

template<class U>
WRL_NOTHROW ComPtr(
   _Inout_ ComPtr<U>&& other, typename ENABLE_IF<__is_convertible_to(U*, T*), void *>
);
```

### <a name="parameters"></a>Parametry

*H*<br/>
Typ *druhého* parametru.

*jiná*<br/>
Objekt typu *U*.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

První konstruktor je výchozí konstruktor, který implictly vytvoří prázdný objekt. Druhý konstruktor určuje [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), který explicitně vytvoří prázdný objekt.

Třetí konstruktor vytvoří objekt z objektu určeného ukazatelem. ComPtr nyní vlastní odkazovalo na paměť a udržuje pro něj počet odkazů.

Čtvrtý a pátý konstruktor jsou kopírovací konstruktory. Pátý konstruktor zkopíruje objekt, pokud je převoditelné na aktuální typ.

Šest a sedmý konstruktor jsou konstruktory Move. Sedmý konstruktor přesune objekt, pokud je převoditelné na aktuální typ.

## <a name="copyto"></a>ComPtr:: CopyTo

Zkopíruje aktuální nebo zadané rozhraní přidružené k tomuto `ComPtr` k zadanému ukazateli.

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

*H*<br/>
Název typu.

*ptr*<br/>
Po dokončení této operace se zobrazí ukazatel na požadované rozhraní.

*riid*<br/>
ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která indikuje, proč se operace implicitního `QueryInterface` nezdařila.

### <a name="remarks"></a>Poznámky

První funkce vrátí kopii ukazatele na rozhraní přidruženého k tomuto `ComPtr`. Tato funkce vždy vrátí S_OK.

Druhá funkce provede operaci `QueryInterface` na rozhraní přidruženém k této `ComPtr` pro rozhraní určené parametrem *riid* .

Třetí funkce provádí operaci `QueryInterface` na rozhraní přidruženém k tomuto `ComPtr` pro základní rozhraní parametru *u* .

## <a name="detach"></a>ComPtr::D etach

Zruší přidružení tohoto objektu `ComPtr` z rozhraní, které představuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní, které bylo reprezentované tímto objektem `ComPtr`.

## <a name="get"></a>ComPtr:: Get

Načte ukazatel na rozhraní, které je přidruženo k tomuto `ComPtr`.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní, které je přidruženo k tomuto `ComPtr`.

## <a name="getaddressof"></a>ComPtr:: GetAddressOf –

Načte adresu datového členu [ptr_](#ptr) , který obsahuje ukazatel na rozhraní reprezentované tímto `ComPtr`.

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Adresa proměnné.

## <a name="internaladdref"></a>ComPtr:: InternalAddRef –

Zvýší počet odkazů rozhraní přidruženého k tomuto `ComPtr`.

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Poznámky

Tato metoda je chráněná.

## <a name="internalrelease"></a>ComPtr:: InternalRelease –

Provede operaci uvolnění modelu COM na rozhraní, které je přidruženo k tomuto `ComPtr`.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Poznámky

Tato metoda je chráněná.

## <a name="operator-ampersand"></a>ComPtr:: operator&amp;

Uvolní rozhraní přidružené k tomuto objektu `ComPtr` a potom načte adresu `ComPtr` objektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Návratová hodnota

Slabý odkaz na aktuální `ComPtr`.

### <a name="remarks"></a>Poznámky

Tato metoda se liší od [ComPtr:: GetAddressOf –](#getaddressof) v tom, že tato metoda uvolní odkaz na ukazatel rozhraní. Použijte `ComPtr::GetAddressOf`, pokud požadujete adresu ukazatele rozhraní, ale nechcete toto rozhraní uvolnit.

## <a name="operator-arrow"></a>ComPtr:: operator-&gt;

Načte ukazatel na typ určený aktuálním parametrem šablony.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na typ určený aktuálním názvem typu šablony.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce odebere nepotřebnou režii způsobenou použitím makra STDMETHOD. Tato funkce zpřístupňuje `IUnknown` typy `private` namísto `virtual`.

## <a name="operator-assign"></a>ComPtr:: operator =

Přiřadí hodnotu aktuálnímu `ComPtr`.

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

*H*<br/>
Třída.

*jiná*<br/>
Odkaz na ukazatel, odkaz nebo rvalue na typ nebo jiný `ComPtr`.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `ComPtr`.

### <a name="remarks"></a>Poznámky

První verze tohoto operátoru přiřadí aktuálnímu `ComPtr`prázdnou hodnotu.

V druhé verzi platí, že pokud ukazatel přiřazení rozhraní není stejný jako aktuální `ComPtr` ukazatel rozhraní, druhý ukazatel rozhraní je přiřazen aktuálnímu `ComPtr`.

Ve třetí verzi je ukazatel přiřazení rozhraní přiřazen aktuálnímu `ComPtr`.

Pokud se ve čtvrté verzi ukazatel rozhraní v hodnotě přiřazení neshoduje s aktuálním `ComPtr` ukazatel rozhraní, je druhý ukazatel rozhraní přiřazen aktuálnímu `ComPtr`.

Pátá verze je operátor kopírování; k aktuálnímu `ComPtr`je přiřazen odkaz na `ComPtr`.

Šestá verze je operátor kopírování, který používá sémantiku přesunutí; odkaz rvalue na `ComPtr`, pokud je nějaký typ statické přetypování a pak se přiřadí k aktuálnímu `ComPtr`.

Sedmá verze je operátor kopírování, který používá sémantiku přesunutí; odkaz rvalue na `ComPtr` typu *U* je statické přetypování a přiřazený k aktuálnímu `ComPtr`.

## <a name="operator-equality"></a>ComPtr:: operator = = – operátor

Určuje, zda jsou dva objekty `ComPtr` stejné.

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

*určitého*<br/>
Odkaz na objekt `ComPtr`.

*b*<br/>
Odkaz na jiný objekt `ComPtr`.

### <a name="return-value"></a>Návratová hodnota

První operátor vrací `true`, pokud je objekt *a* roven objektu *b*; v opačném případě `false`.

Druhý a třetí operátor poskytují `true`, pokud je objekt *a* roven `nullptr`; v opačném případě `false`.

## <a name="operator-inequality"></a>ComPtr:: operator! =

Určuje, zda se dva objekty `ComPtr` neshodují.

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

*určitého*<br/>
Odkaz na objekt `ComPtr`.

*b*<br/>
Odkaz na jiný objekt `ComPtr`.

### <a name="return-value"></a>Návratová hodnota

První operátor vrací `true`, pokud objekt *a* není rovna objektu *b*; v opačném případě `false`.

Druhý a třetí operátor poskytují `true`, pokud objekt *a* není rovna `nullptr`; v opačném případě `false`.

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: operator Microsoft:: WRL::D etails:: BoolType –

Označuje, zda `ComPtr` Správa životnosti objektu rozhraní.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je k tomuto `ComPtr`přidruženo rozhraní, adresa člena data member [BoolStruct –:: member](boolstruct-structure.md#member) ; v opačném případě `nullptr`.

## <a name="ptr"></a>ComPtr::p tr_

Obsahuje ukazatel na rozhraní, které je přidruženo a spravováno tímto `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Poznámky

`ptr_` je interní chráněný datový člen.

## <a name="releaseandgetaddressof"></a>ComPtr:: Releaseandgetaddressof –

Uvolní rozhraní přidružené k tomuto `ComPtr` a potom načte adresu datového členu [ptr_](#ptr) , který obsahuje ukazatel na rozhraní, které bylo vydány.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Adresa datového členu [ptr_](#ptr) této `ComPtr`.

## <a name="reset"></a>ComPtr:: Reset

Uvolní všechny odkazy pro ukazatel na rozhraní, které je přidruženo k tomuto `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Návratová hodnota

Počet vydaných odkazů, pokud existují.

## <a name="swap"></a>ComPtr:: swap

Vyměňuje rozhraní spravované aktuální `ComPtr` s rozhraním spravovaným zadanou `ComPtr`.

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parametry

*í*<br/>
Úloha `ComPtr`.

