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
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498417"
---
# <a name="comptr-class"></a>ComPtr – třída

Vytvoří typ *inteligentního ukazatele* , který představuje rozhraní určené parametrem šablony. `ComPtr`automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, když počet odkazů překročí nulu.

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class ComPtr;

template<class T>
friend class ComPtr;
```

### <a name="parameters"></a>Parametry

*T*<br/>
Rozhraní, které `ComPtr` představuje.

*U*<br/>
Třída, na kterou je aktuální `ComPtr` přítel. (Šablona, která používá tento parametr je chráněná.)

## <a name="remarks"></a>Poznámky

`ComPtr<>`Deklaruje typ, který reprezentuje ukazatel základního rozhraní. Slouží `ComPtr<>` k deklaraci proměnné a následnému použití operátoru přístupu členů (`->`) k přístupu k členské funkci rozhraní.

Další informace o inteligentních ukazatelích naleznete v pododdílu inteligentních ukazatelů COM v tématu [postupy psaní kódu modelu COM](/windows/win32/LearnWin32/com-coding-practices) v knihovně MSDN.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné definice typedef

Name            | Popis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonymum pro typ určený parametrem šablony *T* .

### <a name="public-constructors"></a>Veřejné konstruktory

Name                             | Popis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr:: ComPtr](#comptr)        | Inicializuje novou instanci `ComPtr` třídy. Přetížení poskytují konstruktory Default, Copy, Move a Conversion.
[ComPtr::~ComPtr](#tilde-comptr) | Zruší inicializaci instance `ComPtr`.

### <a name="public-methods"></a>Veřejné metody

Name                                                      | Popis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr:: as](#as)                                         | `ComPtr` Vrátí objekt, který představuje rozhraní identifikované zadaným parametrem šablony.
[ComPtr:: AsIID –](#asiid)                                   | `ComPtr` Vrátí objekt, který představuje rozhraní identifikované zadaným ID rozhraní.
[ComPtr:: AsWeak –](#asweak)                                 | Načte slabý odkaz na aktuální objekt.
[ComPtr:: Attach](#attach)                                 | `ComPtr` Přidruží k typu rozhraní určenému parametrem typu aktuální šablony.
[ComPtr:: CopyTo](#copyto)                                 | Zkopíruje aktuální nebo zadané rozhraní přidružené `ComPtr` k zadanému výstupnímu ukazateli.
[ComPtr::Detach](#detach)                                 | Zruší přidružení této `ComPtr` k rozhraní, které představuje.
[ComPtr:: Get](#get)                                       | Načte ukazatel na rozhraní, které je k tomuto `ComPtr`typu přidruženo.
[ComPtr::GetAddressOf](#getaddressof)                     | Načte adresu datového členu [ptr_](#ptr) , který obsahuje ukazatel na rozhraní reprezentované tímto `ComPtr`.
[ComPtr:: Releaseandgetaddressof –](#releaseandgetaddressof) | Uvolní rozhraní přidružené k tomuto `ComPtr` a potom načte adresu [ptr_](#ptr) datového člena, který obsahuje ukazatel na rozhraní, které bylo vydány.
[ComPtr::Reset](#reset)                                   | Uvolní všechny odkazy pro ukazatel na rozhraní, které je přidruženo k tomuto `ComPtr`.
[ComPtr:: swap](#swap)                                     | Vyměňuje rozhraní spravované pomocí aktuální `ComPtr` s rozhraním spravovaném zadaným. `ComPtr`

### <a name="protected-methods"></a>Chráněné metody

Name                                        | Popis
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr:: InternalAddRef –](#internaladdref)   | Zvýší počet odkazů rozhraní přidruženého k tomuto `ComPtr`.
[ComPtr:: InternalRelease –](#internalrelease) | Provede operaci uvolnění modelu COM na rozhraní, které je přidruženo k tomuto `ComPtr`.

### <a name="public-operators"></a>Veřejné operátory

Name                                                                                           | Popis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr:: operator &](#operator-ampersand)                                                       | Načte adresu aktuálního `ComPtr`.
[ComPtr:: operator->](#operator-arrow)                                                          | Načte ukazatel na typ určený aktuálním parametrem šablony.
[ComPtr:: operator =](#operator-assign)                                                          | Přiřadí hodnotu k aktuálnímu `ComPtr`.
[ComPtr:: operator = = – operátor](#operator-equality)                                                       | Určuje, zda `ComPtr` jsou dva objekty stejné.
[ComPtr:: operator! =](#operator-inequality)                                                     | Určuje, zda `ComPtr` dva objekty nejsou stejné.
[ComPtr:: operator Microsoft:: WRL::D etails:: BoolType –](#operator-microsoft-wrl-details-booltype) | Označuje, zda `ComPtr` je nebo není spravována životnost objektu rozhraní.

### <a name="protected-data-members"></a>Chránění členové dat

Name                 | Popis
-------------------- | ------------------------------------------------------------------------------------------
[ComPtr::p tr_](#ptr) | Obsahuje ukazatel na rozhraní, které je přidruženo a spravováno tímto `ComPtr`.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** Client. h

**Hosting** Microsoft::WRL

## <a name="tilde-comptr"></a>ComPtr:: ~ ComPtr

Zruší inicializaci instance `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="as"></a>ComPtr:: as

`ComPtr` Vrátí objekt, který představuje rozhraní identifikované zadaným parametrem šablony.

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
Rozhraní, které má být reprezentované parametrem *p*.

*p*<br/>
Objekt, který představuje rozhraní určené parametrem *U.* `ComPtr` Parametr *p* nesmí odkazovat na aktuální `ComPtr` objekt.

### <a name="remarks"></a>Poznámky

První šablonou je formulář, který byste měli použít ve svém kódu. Druhá šablona je interní podpůrná specializace, která podporuje C++ jazykové funkce, jako je klíčové slovo pro snížení počtu [automatických](../../cpp/auto-cpp.md) typů.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která označuje chybu.

## <a name="asiid"></a>ComPtr:: AsIID –

`ComPtr` Vrátí objekt, který představuje rozhraní identifikované zadaným ID rozhraní.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*riid*<br/>
ID rozhraní.

*p*<br/>
Pokud má objekt rozhraní, jehož ID je rovno *riid*, dvakrát nepřímý ukazatel na rozhraní určené parametrem *riid* ; v opačném případě ukazatel `IUnknown`na.

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

`ComPtr` Přidruží k typu rozhraní určenému parametrem typu aktuální šablony.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*jiná*<br/>
Typ rozhraní.

## <a name="comptr"></a>ComPtr:: ComPtr

Inicializuje novou instanci `ComPtr` třídy. Přetížení poskytují konstruktory Default, Copy, Move a Conversion.

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

*U*<br/>
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

Zkopíruje aktuální nebo zadané rozhraní přidružené `ComPtr` k zadanému ukazateli.

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
Po dokončení této operace se zobrazí ukazatel na požadované rozhraní.

*riid*<br/>
ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě hodnota HRESULT, která indikuje `QueryInterface` , proč se implicitní operace nezdařila.

### <a name="remarks"></a>Poznámky

První funkce vrátí kopii ukazatele na rozhraní přidružené k tomuto `ComPtr`. Tato funkce vždy vrátí hodnotu S_OK.

Druhá funkce provede `QueryInterface` operaci na rozhraní, které je přidružené k tomuto `ComPtr` pro rozhraní určené parametrem *riid* .

Třetí funkce provede `QueryInterface` operaci na rozhraní, které je přidružené k tomuto `ComPtr` pro základní rozhraní parametru *U* .

## <a name="detach"></a>ComPtr::D etach

Zruší přidružení tohoto `ComPtr` objektu z rozhraní, které představuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní, které bylo reprezentované tímto `ComPtr` objektem.

## <a name="get"></a>ComPtr:: Get

Načte ukazatel na rozhraní, které je k tomuto `ComPtr`typu přidruženo.

```cpp
T* Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní, které je přidruženo k `ComPtr`tomuto.

## <a name="getaddressof"></a>ComPtr::GetAddressOf

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

Uvolní rozhraní přidružené k tomuto `ComPtr` objektu a potom načte adresu `ComPtr` objektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Návratová hodnota

Slabý odkaz na aktuální `ComPtr`.

### <a name="remarks"></a>Poznámky

Tato metoda se liší od [ComPtr:: GetAddressOf –](#getaddressof) v tom, že tato metoda uvolní odkaz na ukazatel rozhraní. Použijte `ComPtr::GetAddressOf` , pokud požadujete adresu ukazatele rozhraní, ale nechcete toto rozhraní uvolnit.

## <a name="operator-arrow"></a>ComPtr:: operator-&gt;

Načte ukazatel na typ určený aktuálním parametrem šablony.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na typ určený aktuálním názvem typu šablony.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce odebere nepotřebnou režii způsobenou použitím makra STDMETHOD. Tato funkce `IUnknown` zpřístupňuje `private` typy místo `virtual`.

## <a name="operator-assign"></a>ComPtr:: operator =

Přiřadí hodnotu k aktuálnímu `ComPtr`.

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

*jiná*<br/>
Odkaz na ukazatel, odkaz nebo rvalue na typ nebo jiný `ComPtr`typ.

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `ComPtr`.

### <a name="remarks"></a>Poznámky

První verze tohoto operátoru přiřadí k aktuální `ComPtr`hodnotě prázdnou hodnotu.

V druhé verzi platí, že pokud ukazatel na přiřazení rozhraní není stejný jako ukazatel na aktuální `ComPtr` rozhraní, druhý ukazatel rozhraní je přiřazen aktuálnímu. `ComPtr`

Ve třetí verzi je ukazatel přiřazení rozhraní přiřazen k aktuálnímu `ComPtr`.

Pokud se ve čtvrté verzi ukazatel rozhraní v hodnotě přiřazení neshoduje s aktuálním `ComPtr` ukazatelem rozhraní, je druhý ukazatel rozhraní přiřazen k aktuálnímu. `ComPtr`

Pátá verze je operátor kopírování; odkaz na `ComPtr` je přiřazen k aktuálnímu `ComPtr`.

Šestá verze je operátor kopírování, který používá sémantiku přesunutí; odkaz rvalue na typ, `ComPtr` Pokud je libovolný typ statické přetypování a pak se přiřadí `ComPtr`k aktuálnímu.

Sedmá verze je operátor kopírování, který používá sémantiku přesunutí; odkaz rvalue na `ComPtr` typ *U* je statické přetypování a přiřazený k aktuálnímu `ComPtr`.

## <a name="operator-equality"></a>ComPtr:: operator = = – operátor

Určuje, zda `ComPtr` jsou dva objekty stejné.

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
Odkaz na `ComPtr` objekt.

*b*<br/>
Odkaz na jiný `ComPtr` objekt.

### <a name="return-value"></a>Návratová hodnota

První operátor výnosy `true` Pokud objekt *a* rovná objektu *b*; v opačném případě `false`.

Druhý a třetí operátory yield `true` Pokud objekt *a* rovná `nullptr`; v opačném případě `false`.

## <a name="operator-inequality"></a>ComPtr:: operator! =

Určuje, zda `ComPtr` dva objekty nejsou stejné.

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
Odkaz na `ComPtr` objekt.

*b*<br/>
Odkaz na jiný `ComPtr` objekt.

### <a name="return-value"></a>Návratová hodnota

První operátor výnosy `true` Pokud objekt *a* není roven objektu *b*; v opačném případě `false`.

Druhý a třetí operátory yield `true` Pokud objekt *a* není roven `nullptr`; v opačném případě `false`.

## <a name="operator-microsoft-wrl-details-booltype"></a>ComPtr:: operator Microsoft:: WRL::D etails:: BoolType –

Označuje, zda `ComPtr` je nebo není spravována životnost objektu rozhraní.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je k tomuto `ComPtr`rozhraní přidruženo rozhraní, adresa `nullptr`člena [BoolStruct –:: member](boolstruct-structure.md#member) DataMember; v opačném případě.

## <a name="ptr"></a>ComPtr::p tr_

Obsahuje ukazatel na rozhraní, které je přidruženo a spravováno tímto `ComPtr`.

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Poznámky

`ptr_`je interní chráněný datový člen.

## <a name="releaseandgetaddressof"></a>ComPtr:: Releaseandgetaddressof –

Uvolní rozhraní přidružené k tomuto `ComPtr` a potom načte adresu [ptr_](#ptr) datového člena, který obsahuje ukazatel na rozhraní, které bylo vydány.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Adresa datového `ComPtr`členu [ptr_](#ptr) .

## <a name="reset"></a>ComPtr:: Reset

Uvolní všechny odkazy pro ukazatel na rozhraní, které je přidruženo k tomuto `ComPtr`.

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Návratová hodnota

Počet vydaných odkazů, pokud existují.

## <a name="swap"></a>ComPtr:: swap

Vyměňuje rozhraní spravované pomocí aktuální `ComPtr` s rozhraním spravovaném zadaným. `ComPtr`

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

