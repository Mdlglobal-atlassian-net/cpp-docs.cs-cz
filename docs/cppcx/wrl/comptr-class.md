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
ms.openlocfilehash: 89c09ede972f5bdd5da1dde810cad31733bdf338
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81372643"
---
# <a name="comptr-class"></a>ComPtr – třída

Vytvoří inteligentní typ *ukazatele,* který představuje rozhraní určené parametrem šablony. `ComPtr`automaticky udržuje počet odkazů pro základní ukazatel rozhraní a uvolní rozhraní, když počet odkazů přejde na nulu.

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
Třída, ke které `ComPtr` je aktuální přítel. (Šablona, která používá tento parametr, je chráněna.)

## <a name="remarks"></a>Poznámky

`ComPtr<>`deklaruje typ, který představuje základní ukazatel rozhraní. Slouží `ComPtr<>` k deklarování proměnné a potom`->`použijte operátor přístupu člena šipky ( ) pro přístup k členské funkci rozhraní.

Další informace o inteligentních ukazatelích naleznete v podčásti "Com Smart Pointers" v tématu [Postupy kódování COM](/windows/win32/LearnWin32/com-coding-practices) v knihovně MSDN.

## <a name="members"></a>Členové

### <a name="public-typedefs"></a>Veřejné typedefs

Name (Název)            | Popis
--------------- | ---------------------------------------------------------------
`InterfaceType` | Synonymum pro typ určený parametrem šablony *T.*

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                             | Popis
-------------------------------- | --------------------------------------------------------------------------------------------------------------------
[ComPtr::ComPtr](#comptr)        | Intializes novou instanci třídy. `ComPtr` Přetížení poskytují výchozí, kopírovat, přesunout a převod konstruktory.
[ComPtr::~ComPtr](#tilde-comptr) | Deinitializes instance `ComPtr`.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                      | Popis
--------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
[ComPtr::As](#as)                                         | Vrátí `ComPtr` objekt, který představuje rozhraní identifikované zadaným parametrem šablony.
[ComPtr::AsIID](#asiid)                                   | Vrátí `ComPtr` objekt, který představuje rozhraní identifikované zadaným ID rozhraní.
[ComPtr::AsWeak](#asweak)                                 | Načte slabý odkaz na aktuální objekt.
[ComPtr::Připojit](#attach)                                 | Přidruží to `ComPtr` k typu rozhraní určenému aktuálním parametrem typu šablony.
[ComPtr::Kopírovat](#copyto)                                 | Zkopíruje aktuální nebo zadané `ComPtr` rozhraní, které je k tomu přidruženo, do zadaného výstupního ukazatele.
[ComPtr::Detach](#detach)                                 | Disassociates `ComPtr` to z rozhraní, které představuje.
[ComPtr::Získat](#get)                                       | Načte ukazatel na rozhraní, které `ComPtr`je k tomu toto přidruženo .
[ComPtr::GetAddressOf](#getaddressof)                     | Načte adresu datového člena [ptr_,](#ptr) který obsahuje ukazatel na `ComPtr`rozhraní reprezentované tímto .
[ComPtr::ReleaseAndGetAddressOf](#releaseandgetaddressof) | Uvolní rozhraní spojené s `ComPtr` tímto a potom načte adresu [ptr_](#ptr) datový člen, který obsahuje ukazatel na rozhraní, které bylo vydáno.
[ComPtr::Reset](#reset)                                   | Uvolní všechny odkazy na ukazatel na rozhraní, které `ComPtr`je k tomu přidruženo .
[ComPtr::Swap](#swap)                                     | Vyměňuje rozhraní spravované `ComPtr` proudem s rozhraním `ComPtr`spravovaným zadaným .

### <a name="protected-methods"></a>Chráněné metody

Name (Název)                                        | Popis
------------------------------------------- | --------------------------------------------------------------------------------
[ComPtr::InternalAddRef](#internaladdref)   | Zintáží počet odkazů rozhraní, `ComPtr`které je k tomu přidruženo .
[ComPtr::InternalRelease](#internalrelease) | Provede operaci vydání com na rozhraní, které je k tomu přidruženo `ComPtr`.

### <a name="public-operators"></a>Veřejné operátory

Name (Název)                                                                                           | Popis
---------------------------------------------------------------------------------------------- | ------------------------------------------------------------------------------------
[ComPtr::&operátora](#operator-ampersand)                                                       | Načte adresu aktuálního `ComPtr`.
[ComPtr::operátor->](#operator-arrow)                                                          | Načte ukazatel na typ určený aktuálním parametrem šablony.
[ComPtr::operátor=](#operator-assign)                                                          | Přiřadí hodnotu aktuálnímu `ComPtr`.
[ComPtr::operátor==](#operator-equality)                                                       | Označuje, `ComPtr` zda jsou dva objekty stejné.
[ComPtr::operátor!=](#operator-inequality)                                                     | Označuje, `ComPtr` zda dva objekty nejsou stejné.
[ComPtr::operátor Microsoft::WRL::Details::BoolType](#operator-microsoft-wrl-details-booltype) | Označuje, zda `ComPtr` a spravuje životnost objektu rozhraní.

### <a name="protected-data-members"></a>Členové chráněných dat

Name (Název)                 | Popis
-------------------- | ------------------------------------------------------------------------------------------
[comptr::ptr_](#ptr) | Obsahuje ukazatel na rozhraní, které je přidruženo `ComPtr`a spravováno tímto .

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtr`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Obor názvů:** Microsoft::WRL

## <a name="comptrcomptr"></a><a name="tilde-comptr"></a>ComPtr::~ComPtr

Deinitializes instance `ComPtr`.

```cpp
WRL_NOTHROW ~ComPtr();
```

## <a name="comptras"></a><a name="as"></a>ComPtr::As

Vrátí `ComPtr` objekt, který představuje rozhraní identifikované zadaným parametrem šablony.

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
Rozhraní, které má být reprezentováno parametrem *p*.

*P*<br/>
Objekt, `ComPtr` který představuje rozhraní určené parametrem *U*. Parametr *p* nesmí odkazovat `ComPtr` na aktuální objekt.

### <a name="remarks"></a>Poznámky

První šablona je formulář, který byste měli použít v kódu. Druhá šablona je interní, pomocná specializace, která podporuje funkce jazyka C++, jako je například klíčové slovo [automatického](../../cpp/auto-cpp.md) odpočtu typu.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="comptrasiid"></a><a name="asiid"></a>ComPtr::AsIID

Vrátí `ComPtr` objekt, který představuje rozhraní identifikované zadaným ID rozhraní.

```cpp
WRL_NOTHROW HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IUnknown>* p
) const;
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
ID rozhraní.

*P*<br/>
Pokud má objekt rozhraní, jehož ID se rovná *riid*, dvojnásob-nepřímý ukazatel na rozhraní určené *riid* parametr; v opačném případě `IUnknown`ukazatel na .

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="comptrasweak"></a><a name="asweak"></a>ComPtr::AsWeak

Načte slabý odkaz na aktuální objekt.

```cpp
HRESULT AsWeak(
   _Out_ WeakRef* pWeakRef
);
```

### <a name="parameters"></a>Parametry

*pWeakRef*<br/>
Po dokončení této operace ukazatel na slabý referenční objekt.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje chybu.

## <a name="comptrattach"></a><a name="attach"></a>ComPtr::Připojit

Přidruží to `ComPtr` k typu rozhraní určenému aktuálním parametrem typu šablony.

```cpp
void Attach(
   _In_opt_ InterfaceType* other
);
```

### <a name="parameters"></a>Parametry

*Další*<br/>
Typ rozhraní.

## <a name="comptrcomptr"></a><a name="comptr"></a>ComPtr::ComPtr

Intializes novou instanci třídy. `ComPtr` Přetížení poskytují výchozí, kopírovat, přesunout a převod konstruktory.

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
Typ *jiného* parametru.

*Další*<br/>
Objekt typu *U*.

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

První konstruktor je výchozí konstruktor, který implictly vytvoří prázdný objekt. Druhý konstruktor určuje [__nullptr](../../extensions/nullptr-cpp-component-extensions.md), který explicitně vytvoří prázdný objekt.

Třetí konstruktor vytvoří objekt z objektu určeného ukazatelem. ComPtr nyní vlastní špičaté paměti a udržuje počet odkazů na něj.

Čtvrtý a pátý konstruktory jsou kopie konstruktory. Pátý konstruktor zkopíruje objekt, pokud je konvertibilní na aktuální typ.

Šestý a sedmý konstruktory jsou přesunout konstruktory. Sedmý konstruktor přesune objekt, pokud je konvertibilní na aktuální typ.

## <a name="comptrcopyto"></a><a name="copyto"></a>ComPtr::Kopírovat

Zkopíruje aktuální nebo zadané `ComPtr` rozhraní, které je k tomu přidruženo, na zadaný ukazatel.

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

*Ptr*<br/>
Po dokončení této operace ukazatel na požadované rozhraní.

*riid řekl:*<br/>
ID rozhraní.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který označuje, `QueryInterface` proč se nezdařila implicitní operace.

### <a name="remarks"></a>Poznámky

První funkce vrátí kopii ukazatele na rozhraní, `ComPtr`které je k tomu přidruženo . Tato funkce vždy vrátí S_OK.

Druhá funkce provádí `QueryInterface` operaci na rozhraní, `ComPtr` které je k tomu přidruženo, pro rozhraní určené parametrem *riid.*

Třetí funkce provádí `QueryInterface` operaci na rozhraní `ComPtr` s tím spojené pro základní rozhraní *u* parametru.

## <a name="comptrdetach"></a><a name="detach"></a>ComPtr::Detach

Disassociates `ComPtr` tento objekt z rozhraní, které představuje.

```cpp
T* Detach();
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní, které bylo `ComPtr` reprezentováno tímto objektem.

## <a name="comptrget"></a><a name="get"></a>ComPtr::Získat

Načte ukazatel na rozhraní, které `ComPtr`je k tomu toto přidruženo .

```cpp
T* Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na rozhraní, které `ComPtr`je k tomu přidruženo .

## <a name="comptrgetaddressof"></a><a name="getaddressof"></a>ComPtr::GetAddressOf

Načte adresu datového člena [ptr_,](#ptr) který obsahuje ukazatel na `ComPtr`rozhraní reprezentované tímto .

```cpp
T* const* GetAddressOf() const;
T** GetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Adresa proměnné.

## <a name="comptrinternaladdref"></a><a name="internaladdref"></a>ComPtr::InternalAddRef

Zintáží počet odkazů rozhraní, `ComPtr`které je k tomu přidruženo .

```cpp
void InternalAddRef() const;
```

### <a name="remarks"></a>Poznámky

Tato metoda je chráněna.

## <a name="comptrinternalrelease"></a><a name="internalrelease"></a>ComPtr::InternalRelease

Provede operaci vydání com na rozhraní, které je k tomu přidruženo `ComPtr`.

```cpp
void InternalRelease();
```

### <a name="remarks"></a>Poznámky

Tato metoda je chráněna.

## <a name="comptroperatoramp"></a><a name="operator-ampersand"></a>ComPtr::operátor&amp;

Uvolní rozhraní přidružené k `ComPtr` tomuto objektu a `ComPtr` potom načte adresu objektu.

```cpp
Details::ComPtrRef<WeakRef> operator&()

const Details::ComPtrRef<const WeakRef> operator&() const
```

### <a name="return-value"></a>Návratová hodnota

Slabý odkaz na `ComPtr`proud .

### <a name="remarks"></a>Poznámky

Tato metoda se liší od [ComPtr::GetAddressOf](#getaddressof) v tom, že tato metoda uvolní odkaz na ukazatel rozhraní. Použijte, `ComPtr::GetAddressOf` pokud požadujete adresu ukazatele rozhraní, ale nechcete uvolnit toto rozhraní.

## <a name="comptroperator-gt"></a><a name="operator-arrow"></a>ComPtr::operátor-&gt;

Načte ukazatel na typ určený aktuálním parametrem šablony.

```cpp
WRL_NOTHROW Microsoft::WRL::Details::RemoveIUnknown<InterfaceType>* operator->() const;
```

### <a name="return-value"></a>Návratová hodnota

Ukazatel na typ určený aktuálním názvem typu šablony.

### <a name="remarks"></a>Poznámky

Tato pomocná funkce odstraňuje zbytečné režie způsobené použitím makra STDMETHOD. Tato funkce `IUnknown` `private` umožňuje `virtual`typy namísto .

## <a name="comptroperator"></a><a name="operator-assign"></a>ComPtr::operátor=

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

*U*<br/>
Třída.

*Další*<br/>
Odkaz na ukazatel, odkaz nebo rvalue `ComPtr`na typ nebo jiný .

### <a name="return-value"></a>Návratová hodnota

Odkaz na aktuální `ComPtr`.

### <a name="remarks"></a>Poznámky

První verze tohoto operátoru přiřadí prázdnou `ComPtr`hodnotu aktuálnímu .

V druhé verzi, pokud ukazatel přiřazování rozhraní `ComPtr` není stejný jako aktuální ukazatel rozhraní, druhý ukazatel rozhraní je přiřazen aktuálnímu `ComPtr`.

Ve třetí verzi je ukazatel přiřazovacího rozhraní přiřazen aktuálnímu `ComPtr`.

Pokud ukazatel rozhraní přiřazovací hodnoty není ve čtvrté verzi `ComPtr` stejný jako aktuální ukazatel rozhraní, `ComPtr`je druhému ukazateli rozhraní přiřazen aktuální ukazatel rozhraní .

Pátá verze je operátor kopírování; odkaz na `ComPtr` a je přiřazen `ComPtr`k aktuálnímu .

Šestá verze je operátor kopírování, který používá přesunout sémantiku; rvalue odkaz na `ComPtr` a if některý typ je statický `ComPtr`přetypování a pak přiřazen k proudu .

Sedmá verze je operátor kopírování, který používá přesunout sémantiku; rvalue odkaz na `ComPtr` typ *U* je statický přetypování `ComPtr`pak a přiřazenka aktuální .

## <a name="comptroperator"></a><a name="operator-equality"></a>ComPtr::operátor==

Označuje, `ComPtr` zda jsou dva objekty stejné.

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

*A*<br/>
Odkaz na `ComPtr` objekt.

*B*<br/>
Odkaz na `ComPtr` jiný objekt.

### <a name="return-value"></a>Návratová hodnota

První operátor `true` dává, pokud objekt *a* se rovná *objektu b*; v `false`opačném případě .

Druhý a třetí `true` operátor výnos, pokud `nullptr`objekt *a* se rovná ; v `false`opačném případě .

## <a name="comptroperator"></a><a name="operator-inequality"></a>ComPtr::operátor!=

Označuje, `ComPtr` zda dva objekty nejsou stejné.

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

*A*<br/>
Odkaz na `ComPtr` objekt.

*B*<br/>
Odkaz na `ComPtr` jiný objekt.

### <a name="return-value"></a>Návratová hodnota

První operátor `true` dává, pokud objekt *a* není rovna *objektu b*; v `false`opačném případě .

Druhý a třetí `true` operátor výnos, pokud `nullptr`objekt *a* není rovna ; v `false`opačném případě .

## <a name="comptroperator-microsoftwrldetailsbooltype"></a><a name="operator-microsoft-wrl-details-booltype"></a>ComPtr::operátor Microsoft::WRL::Details::BoolType

Označuje, zda `ComPtr` a spravuje životnost objektu rozhraní.

```cpp
WRL_NOTHROW operator Microsoft::WRL::Details::BoolType() const;
```

### <a name="return-value"></a>Návratová hodnota

Pokud je k tomu `ComPtr`přidruženo rozhraní , adresa datového člena [BoolStruct::Member](boolstruct-structure.md#member) data; v `nullptr`opačném případě .

## <a name="comptrptr_"></a><a name="ptr"></a>comptr::ptr_

Obsahuje ukazatel na rozhraní, které je přidruženo `ComPtr`a spravováno tímto .

```cpp
InterfaceType *ptr_;
```

### <a name="remarks"></a>Poznámky

`ptr_`je interní, chráněný datový člen.

## <a name="comptrreleaseandgetaddressof"></a><a name="releaseandgetaddressof"></a>ComPtr::ReleaseAndGetAddressOf

Uvolní rozhraní spojené s `ComPtr` tímto a potom načte adresu [ptr_](#ptr) datový člen, který obsahuje ukazatel na rozhraní, které bylo vydáno.

```cpp
T** ReleaseAndGetAddressOf();
```

### <a name="return-value"></a>Návratová hodnota

Adresa [ptr_](#ptr) datového člena `ComPtr`tohoto .

## <a name="comptrreset"></a><a name="reset"></a>ComPtr::Obnovit

Uvolní všechny odkazy na ukazatel na rozhraní, které `ComPtr`je k tomu přidruženo .

```cpp
unsigned long Reset();
```

### <a name="return-value"></a>Návratová hodnota

Počet odkazů, které byly uvolněny, pokud existuje.

## <a name="comptrswap"></a><a name="swap"></a>ComPtr::Swap

Vyměňuje rozhraní spravované `ComPtr` proudem s rozhraním `ComPtr`spravovaným zadaným .

```cpp
void Swap(
   _Inout_ ComPtr&& r
);

void Swap(
   _Inout_ ComPtr& r
);
```

### <a name="parameters"></a>Parametry

*R*<br/>
Úloha `ComPtr`.
