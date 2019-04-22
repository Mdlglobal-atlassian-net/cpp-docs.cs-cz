---
title: WeakRef – třída
ms.date: 10/03/2018
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
- client/Microsoft::WRL::WeakRef::~WeakRef
- client/Microsoft::WRL::WeakRef::As
- client/Microsoft::WRL::WeakRef::AsIID
- client/Microsoft::WRL::WeakRef::CopyTo
- client/Microsoft::WRL::WeakRef::operator&
- client/Microsoft::WRL::WeakRef::WeakRef
helpviewer_keywords:
- Microsoft::WRL::WeakRef class
- Microsoft::WRL::WeakRef::~WeakRef, destructor
- Microsoft::WRL::WeakRef::As method
- Microsoft::WRL::WeakRef::AsIID method
- Microsoft::WRL::WeakRef::CopyTo method
- Microsoft::WRL::WeakRef::operator& operator
- Microsoft::WRL::WeakRef::WeakRef, constructor
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
ms.openlocfilehash: 9616fcffac0b92d5ac6d96cfe5f4119f3a3b180f
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58786918"
---
# <a name="weakref-class"></a>WeakRef – třída

Představuje *nestálý odkaz* , který lze používat pouze modulu Windows Runtime, ne klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name|Popis|
|----------|-----------------|
|[WeakRef::WeakRef – konstruktor](#weakref)|Inicializuje novou instanci třídy `WeakRef` třídy.|
|[WeakRef::~WeakRef – destruktor](#tilde-weakref)|Zruší inicializaci aktuální instance `WeakRef` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Name|Popis|
|----------|-----------------|
|[WeakRef::As – metoda](#as)|Nastaví zadaný `ComPtr` parametr ukazatele k reprezentaci zadané rozhraní.|
|[WeakRef::AsIID – metoda](#asiid)|Nastaví zadaný `ComPtr` parametr ukazatele představující ID zadané rozhraní.|
|[WeakRef::CopyTo – metoda](#copyto)|Přiřadí ukazatel rozhraní, pokud je k dispozici k proměnné zadané ukazatele.|

### <a name="public-operators"></a>Veřejné operátory

|Name|Popis|
|----------|-----------------|
|[WeakRef::operator& – operátor](#operator-ampersand-operator)|Vrátí `ComPtrRef` objekt, který představuje aktuální `WeakRef` objektu.|

## <a name="remarks"></a>Poznámky

A `WeakRef` udržuje objekt *silného odkazu*, který je přidružený k objektu a může být platný nebo neplatný. Volání `As()` nebo `AsIID()` metodu k získání silného odkazu. Silný odkaz je platný, má přístup k přidruženého objektu. Když je neplatný silný odkaz (`nullptr`), přidruženého objektu není dostupný.

A `WeakRef` objekt se obvykle používá k reprezentaci objektu, jehož existence je řízena vnějším vláknem nebo aplikací. Například sestavit `WeakRef` objekt z odkazu na objekt souboru. Když je soubor otevřen, silný odkaz je platný. Ale pokud se soubor zavře, silný odkaz níže uvedených situací.

Všimněte si, že dojde ke změně chování v [jako](#as), [asiid –](#asiid) a [CopyTo](#copyto) metody ve Windows 10 SDK. Dříve, po volání některé z těchto metod, můžete zkontrolovat, `WeakRef` pro `nullptr` k určení, pokud silného odkazu byl úspěšně získán, stejně jako v následujícím kódu:

```cpp
WeakRef wr;
strongComptrRef.AsWeak(&wr);

// Now suppose that the object strongComPtrRef points to no longer exists
// and the following code tries to get a strong ref from the weak ref:
ComPtr<ISomeInterface> strongRef;
HRESULT hr = wr.As(&strongRef);

// This check won't work with the Windows 10 SDK version of the library.
// Check the input pointer instead.
if(wr == nullptr)
{
    wprintf(L"Couldn’t get strong ref!");
}
```

Ve výše uvedeném kódu nefunguje při použití Windows 10 SDK (nebo novější). Místo toho zkontrolujte ukazatel, který byl předán pro `nullptr`.

```cpp
if (strongRef == nullptr)
{
    wprintf(L"Couldn't get strong ref!");
}
```

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`ComPtr`

`WeakRef`

## <a name="requirements"></a>Požadavky

**Záhlaví:** client.h

**Namespace:** Microsoft::WRL

## <a name="tilde-weakref"></a>WeakRef:: ~ WeakRef – destruktor

Zruší inicializaci aktuální instance `WeakRef` třídy.

```cpp
~WeakRef();
```

## <a name="as"></a>Weakref::AS – metoda

Nastaví zadaný `ComPtr` parametr ukazatele k reprezentaci zadané rozhraní.

```cpp
template<typename U>
HRESULT As(
   _Out_ ComPtr<U>* ptr
);

template<typename U>
HRESULT As(
   _Out_ Details::ComPtrRef<ComPtr<U>> ptr
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Identifikátor rozhraní.

*ptr*<br/>
Když tato operace dokončí, objekt, který představuje parametr *U*.

### <a name="return-value"></a>Návratová hodnota

- Pokud je tato operace úspěšná; S_OK v opačném případě HRESULT, který označuje důvod operace nebyla úspěšná, a *ptr* je nastavena na `nullptr`.

- Pokud tato operace úspěšná, ale aktuální S_OK `WeakRef` objekt již byl uvolněn. Parametr *ptr* je nastavena na `nullptr`.

- Pokud tato operace úspěšná, ale aktuální S_OK `WeakRef` objekt není odvozen z parametru *U*. Parametr *ptr* je nastavena na `nullptr`.

### <a name="remarks"></a>Poznámky

Je vygenerován chybu, pokud parametr *U* je `IWeakReference`, nebo není odvozen od `IInspectable`.

První šablona je formulář, který by měl používat ve vašem kódu. Druhá šablona se osobní a specializace pomocné rutiny, podporující funkcí jazyka C++, jako [automaticky](../../cpp/auto-cpp.md) klíčovým slovem odvození typu.

Od verze Windows 10 SDK, tato metoda nenastaví `WeakRef` instance na `nullptr` Pokud nebylo možné získat nestálý odkaz, takže byste se měli vyhnout kontroly chyb kódu, který kontroluje `WeakRef` pro `nullptr`. Místo toho zkontrolujte *ptr* pro `nullptr`.

## <a name="asiid"></a>Weakref::asiid – metoda

Nastaví zadaný `ComPtr` parametr ukazatele představující ID zadané rozhraní.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*ptr*<br/>
Když tato operace dokončí, objekt, který představuje parametr *riid*.

### <a name="return-value"></a>Návratová hodnota

- Pokud je tato operace úspěšná; S_OK v opačném případě HRESULT, který označuje důvod operace nebyla úspěšná, a *ptr* je nastavena na `nullptr`.

- Pokud tato operace úspěšná, ale aktuální S_OK `WeakRef` objekt již byl uvolněn. Parametr *ptr* je nastavena na `nullptr`.

- Pokud tato operace úspěšná, ale aktuální S_OK `WeakRef` objekt není odvozen z parametru *riid*. Parametr *ptr* je nastavena na `nullptr`. (Další informace najdete v části poznámky.)

### <a name="remarks"></a>Poznámky

Je vygenerován chybu, pokud parametr *riid* není odvozen od `IInspectable`. Tato chyba nahrazuje návratovou hodnotu.

První šablona je formulář, který by měl používat ve vašem kódu. Druhá šablona (není vidět, ale deklarované v souboru hlaviček) je interní, specializace pomocné rutiny, podporující funkcí jazyka C++, jako [automaticky](../../cpp/auto-cpp.md) klíčovým slovem odvození typu.

Od verze Windows 10 SDK, tato metoda nenastaví `WeakRef` instance na `nullptr` Pokud nebylo možné získat nestálý odkaz, takže byste se měli vyhnout kontroly chyb kódu, který kontroluje `WeakRef` pro `nullptr`. Místo toho zkontrolujte *ptr* pro `nullptr`.

## <a name="copyto"></a>Weakref::CopyTo – metoda

Přiřadí ukazatel rozhraní, pokud je k dispozici k proměnné zadané ukazatele.

```cpp
HRESULT CopyTo(
   REFIID riid,
   _Deref_out_ IInspectable** ptr
);

template<typename U>
HRESULT CopyTo(
   _Deref_out_ U** ptr
);

HRESULT CopyTo(
   _Deref_out_ IWeakReference** ptr
);
```

### <a name="parameters"></a>Parametry

*U*<br/>
Ukazatel `IInspectable` rozhraní. Je vygenerován chybu, pokud *U* není odvozen od `IInspectable`.

*riid*<br/>
Identifikátor rozhraní. Je vygenerován chybu, pokud *riid* není odvozen od `IWeakReference`.

*ptr*<br/>
Dvakrát nepřímé ukazatel na `IInspectable` nebo `IWeakReference`.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby. Další informace najdete v tématu **poznámky**.

### <a name="remarks"></a>Poznámky

Vrácená hodnota S_OK znamená, že tato operace proběhla úspěšně, ale neukazuje, jestli se přeložila na silný odkaz nestálý odkaz. Pokud se vrátí hodnotu S_OK, otestujte tento parametr *p* je silný odkaz; to znamená, že parametr *p* není roven `nullptr`.

Od verze Windows 10 SDK, tato metoda nenastaví `WeakRef` instance na `nullptr` Pokud nebylo možné získat nestálý odkaz, takže byste se měli vyhnout Chyba při kontrole kódu, který kontroluje `WeakRef` pro `nullptr`. Místo toho zkontrolujte *ptr* pro `nullptr`.

## <a name="operator-ampersand-operator"></a>WeakRef::operator&amp; – operátor

Vrátí `ComPtrRef` objekt, který představuje aktuální `WeakRef` objektu.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Návratová hodnota

A `ComPtrRef` objekt, který představuje aktuální `WeakRef` objektu.

### <a name="remarks"></a>Poznámky

Toto je interní pomocné operátor, který není určena k použití ve vašem kódu.

## <a name="weakref"></a>Weakref::weakref – konstruktor

Inicializuje novou instanci třídy `WeakRef` třídy.

```cpp
WeakRef();
WeakRef(
   decltype(__nullptr)
);

WeakRef(
   _In_opt_ IWeakReference* ptr
);

WeakRef(
   const ComPtr<IWeakReference>& ptr
);

WeakRef(
   const WeakRef& ptr
);

WeakRef(
   _Inout_ WeakRef&& ptr
);
```

### <a name="parameters"></a>Parametry

*ptr*<br/>
Ukazatel, odkaz nebo odkaz rvalue na existující objekt, který inicializuje aktuální `WeakRef` objektu.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje prázdnou `WeakRef` objektu. Druhý konstruktor inicializuje `WeakRef` z ukazatele na objekt `IWeakReference` rozhraní. Třetí konstruktor inicializuje `WeakRef` z odkazu na objekt `ComPtr<IWeakReference>` objektu. Čtvrtý a pátý konstruktor inicializuje `WeakRef` objektu z jiného `WeakRef` objektu.
