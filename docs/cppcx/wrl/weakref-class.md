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
ms.openlocfilehash: 681f5a64c3e2902c66facbd4f0ac3a3663a7e79d
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374259"
---
# <a name="weakref-class"></a>WeakRef – třída

Představuje *slabý odkaz,* který může být použit pouze prostředím Windows Runtime, nikoli klasickým com. Slabý odkaz představuje objekt, který může nebo nemusí být přístupný.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakRef : public ComPtr<IWeakReference>;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[WeakRef::WeakRef – konstruktor](#weakref)|Inicializuje novou instanci třídy. `WeakRef`|
|[WeakRef::~WeakRef – destruktor](#tilde-weakref)|Deinitializes aktuální instance `WeakRef` třídy.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[WeakRef::As – metoda](#as)|Nastaví `ComPtr` zadaný parametr ukazatele tak, aby představoval zadané rozhraní.|
|[WeakRef::AsIID – metoda](#asiid)|Nastaví `ComPtr` zadaný parametr ukazatele tak, aby představoval zadané ID rozhraní.|
|[WeakRef::CopyTo – metoda](#copyto)|Přiřadí ukazatel rozhraní, pokud je k dispozici, k zadané proměnné ukazatele.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[WeakRef::operator& – operátor](#operator-ampersand-operator)|Vrátí `ComPtrRef` objekt, který `WeakRef` představuje aktuální objekt.|

## <a name="remarks"></a>Poznámky

Objekt `WeakRef` zachová *silnou referenci*, která je přidružena k objektu a může být platná nebo neplatná. Volání `As()` nebo `AsIID()` metoda získat silný odkaz. Pokud je silný odkaz platný, může získat přístup k přidruženému objektu. Pokud je silný odkaz`nullptr`neplatný ( ), přidružený objekt je nepřístupný.

Objekt `WeakRef` se obvykle používá k reprezentaci objektu, jehož existence je řízena externím vláknem nebo aplikací. Například vytvořte `WeakRef` objekt z odkazu na objekt souboru. Když je soubor otevřený, silný odkaz je platný. Pokud je však soubor uzavřen, silný odkaz se stane neplatným.

Všimněte si, že je změna chování v [As](#as), [AsIID](#asiid) a [CopyTo](#copyto) metody v systému Windows 10 SDK. Dříve po volání některé z těchto metod, můžete zkontrolovat `WeakRef` pro `nullptr` zjistit, zda byl úspěšně získán silný odkaz, jako v následujícím kódu:

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

Výše uvedený kód nefunguje při použití sady Windows 10 SDK (nebo novější). Místo toho zkontrolujte ukazatel, `nullptr`který byl předán v pro .

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

**Obor názvů:** Microsoft::WRL

## <a name="weakrefweakref-destructor"></a><a name="tilde-weakref"></a>WeakRef::~WeakRef Destructor

Deinitializes aktuální instance `WeakRef` třídy.

```cpp
~WeakRef();
```

## <a name="weakrefas-method"></a><a name="as"></a>WeakRef::Jako metoda

Nastaví `ComPtr` zadaný parametr ukazatele tak, aby představoval zadané rozhraní.

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
ID rozhraní.

*Ptr*<br/>
Po dokončení této operace objekt, který představuje parametr *U*.

### <a name="return-value"></a>Návratová hodnota

- S_OK pokud tato operace proběhne úspěšně; v opačném případě HRESULT, který označuje důvod, proč `nullptr`se operace nezdařila a *ptr* je nastavena na .

- S_OK pokud tato operace proběhne `WeakRef` úspěšně, ale aktuální objekt již byl vydán. Parametr *ptr* je `nullptr`nastaven na .

- S_OK pokud je tato operace `WeakRef` úspěšná, ale aktuální objekt není odvozen z parametru *U*. Parametr *ptr* je `nullptr`nastaven na .

### <a name="remarks"></a>Poznámky

Chyba je emitován, `IWeakReference`pokud je parametr `IInspectable` *U* , nebo není odvozen z .

První šablona je formulář, který byste měli použít v kódu. Druhá šablona je interní, pomocná specializace, která podporuje funkce jazyka C++, jako je například klíčové slovo [automatického](../../cpp/auto-cpp.md) odpočtu typu.

Počínaje windows 10 SDK, tato metoda `WeakRef` nenastaví instanci, pokud `nullptr` nelze získat slabý odkaz, takže byste `WeakRef` `nullptr`se měli vyhnout kódu kontroly chyb, který kontroluje pro . Místo toho zkontrolujte `nullptr` *ptr* pro .

## <a name="weakrefasiid-method"></a><a name="asiid"></a>WeakRef::Asiid metoda

Nastaví `ComPtr` zadaný parametr ukazatele tak, aby představoval zadané ID rozhraní.

```cpp
HRESULT AsIID(
   REFIID riid,
   _Out_ ComPtr<IInspectable>* ptr
);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
ID rozhraní.

*Ptr*<br/>
Po dokončení této operace objekt, který představuje parametr *riid*.

### <a name="return-value"></a>Návratová hodnota

- S_OK pokud tato operace proběhne úspěšně; v opačném případě HRESULT, který označuje důvod, proč `nullptr`se operace nezdařila a *ptr* je nastavena na .

- S_OK pokud tato operace proběhne `WeakRef` úspěšně, ale aktuální objekt již byl vydán. Parametr *ptr* je `nullptr`nastaven na .

- S_OK pokud tato operace proběhne `WeakRef` úspěšně, ale aktuální objekt není odvozen z *parametru riid*. Parametr *ptr* je `nullptr`nastaven na . (Další informace naleznete v tématu Poznámky.)

### <a name="remarks"></a>Poznámky

Chyba je emitován, pokud parametr *riid* není odvozen z `IInspectable`. Tato chyba nahrazuje vrácenou hodnotu.

První šablona je formulář, který byste měli použít v kódu. Druhá šablona (není zobrazena zde, ale deklarována v souboru záhlaví) je interní specializace pomocníka, která podporuje funkce jazyka C++, jako je například klíčové slovo [automatického](../../cpp/auto-cpp.md) odpočtu typu.

Počínaje windows 10 SDK, tato metoda `WeakRef` nenastaví instanci, pokud `nullptr` nelze získat slabý odkaz, takže byste `WeakRef` `nullptr`se měli vyhnout kódu kontroly chyb, který kontroluje pro . Místo toho zkontrolujte `nullptr` *ptr* pro .

## <a name="weakrefcopyto-method"></a><a name="copyto"></a>weakref::metoda copyto

Přiřadí ukazatel rozhraní, pokud je k dispozici, k zadané proměnné ukazatele.

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
Ukazatel `IInspectable` rozhraní. Chyba je emitován, pokud `IInspectable` *U* není odvozen od .

*riid řekl:*<br/>
ID rozhraní. Chyba je emitován, pokud *riid* není odvozen z `IWeakReference`.

*Ptr*<br/>
Dvojnásob nepřímý ukazatel na `IInspectable` nebo `IWeakReference`.

### <a name="return-value"></a>Návratová hodnota

S_OK v případě úspěchu; jinak HRESULT, který popisuje selhání. Další informace naleznete v **tématu Poznámky**.

### <a name="remarks"></a>Poznámky

Vrácená hodnota S_OK znamená, že tato operace byla úspěšná, ale neznamená, zda byl slabý odkaz vyřešen na silný odkaz. Pokud je vrácena S_OK, otestujte, že parametr *p* je silný odkaz; to znamená, *p* že parametr p `nullptr`se nerovná .

Počínaje windows 10 SDK, tato metoda `WeakRef` nenastaví instanci, pokud `nullptr` nelze získat slabý odkaz, takže `WeakRef` byste `nullptr`se měli vyhnout kódu kontroly chyb, který kontroluje pro . Místo toho zkontrolujte `nullptr` *ptr* pro .

## <a name="weakrefoperatoramp-operator"></a><a name="operator-ampersand-operator"></a>WeakRef::Operátor&amp; operátoru

Vrátí `ComPtrRef` objekt, který `WeakRef` představuje aktuální objekt.

```cpp
Details::ComPtrRef<WeakRef> operator&() throw()
```

### <a name="return-value"></a>Návratová hodnota

Objekt, `ComPtrRef` který představuje `WeakRef` aktuální objekt.

### <a name="remarks"></a>Poznámky

Toto je interní pomocný operátor, který není určen pro použití v kódu.

## <a name="weakrefweakref-constructor"></a><a name="weakref"></a>WeakRef::Konstruktor WeakRef

Inicializuje novou instanci třídy. `WeakRef`

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

*Ptr*<br/>
Ukazatel, odkaz nebo rvalue odkaz na existující objekt, který `WeakRef` inicializuje aktuální objekt.

### <a name="remarks"></a>Poznámky

První konstruktor inicializuje `WeakRef` prázdný objekt. Druhý konstruktor inicializuje `WeakRef` objekt z ukazatele `IWeakReference` na rozhraní. Třetí konstruktor inicializuje `WeakRef` objekt z odkazu `ComPtr<IWeakReference>` na objekt. Čtvrtý a pátý konstruktory inicializuje `WeakRef` `WeakRef` objekt z jiného objektu.
