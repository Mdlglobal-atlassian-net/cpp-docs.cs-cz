---
title: WeakReference – třída
ms.date: 09/24/2018
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::Details::WeakReference
- implements/Microsoft::WRL::Details::WeakReference::DecrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::IncrementStrongReference
- implements/Microsoft::WRL::Details::WeakReference::Resolve
- implements/Microsoft::WRL::Details::WeakReference::SetUnknown
- implements/Microsoft::WRL::Details::WeakReference::~WeakReference
- implements/Microsoft::WRL::Details::WeakReference::WeakReference
helpviewer_keywords:
- Microsoft::WRL::Details::WeakReference class
- Microsoft::WRL::Details::WeakReference::DecrementStrongReference method
- Microsoft::WRL::Details::WeakReference::IncrementStrongReference method
- Microsoft::WRL::Details::WeakReference::Resolve method
- Microsoft::WRL::Details::WeakReference::SetUnknown method
- Microsoft::WRL::Details::WeakReference::~WeakReference, destructor
- Microsoft::WRL::Details::WeakReference::WeakReference, constructor
ms.assetid: 3f4c956b-dbbd-49b1-8cfa-9509a9956c97
ms.openlocfilehash: a80c0ec14da2a955a95ac84dd3975212ef20ae04
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81374221"
---
# <a name="weakreference-class"></a>WeakReference – třída

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference;
```

## <a name="remarks"></a>Poznámky

Představuje *slabý odkaz,* který lze použít s prostředím Windows Runtime nebo klasické com. Slabý odkaz představuje objekt, který může nebo nemusí být přístupný.

Objekt `WeakReference` zachová *silný odkaz*, což je ukazatel na objekt a *počet silných odkazů*, což je počet `Resolve()` kopií silného odkazu, které byly distribuovány metodou. Zatímco počet silných odkazů je nenulová, silný odkaz je platný a objekt je přístupný. Pokud se počet silných odkazů změní na nulu, silný odkaz je neplatný a objekt je nepřístupný.

Objekt `WeakReference` se obvykle používá k reprezentaci objektu, jehož existence je řízena externím vláknem nebo aplikací. Například vytvořte `WeakReference` objekt z odkazu na objekt souboru. Když je soubor otevřený, silný odkaz je platný. Pokud je však soubor uzavřen, silný odkaz se stane neplatným.

Metody `WeakReference` jsou bezpečné pro přístup z více vláken.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Name (Název)                                                  | Popis
----------------------------------------------------- | ---------------------------------------------------------------------------
[WeakReference::WeakReference](#weakreference)        | Inicializuje novou instanci třídy. `WeakReference`
[WeakReference::~WeakReference](#tilde-weakreference) | Deinitializes (zničí) aktuální instance `WeakReference` třídy.

### <a name="public-methods"></a>Veřejné metody

Name (Název)                                                                 | Popis
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | Sníží počet silných odkazů aktuálního `WeakReference` objektu.
[WeakReference::IncrementStrongReference](#incrementstrongreference) | Zintáží silný počet odkazů `WeakReference` aktuálního objektu.
[WeakReference::Vyřešit](#resolve)                                   | Nastaví zadaný ukazatel na aktuální silnou referenční hodnotu, pokud je počet silných odkazů nenulový.
[WeakReference::SetUnknown](#setunknown)                             | Nastaví silný odkaz `WeakReference` aktuálního objektu na zadaný ukazatel rozhraní.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WeakReference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Obor názvů:** Microsoft::WRL::Details

## <a name="weakreferenceweakreference"></a><a name="tilde-weakreference"></a>WeakReference::~WeakReference

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Deinitializes aktuální instance `WeakReference` třídy.

## <a name="weakreferencedecrementstrongreference"></a><a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Poznámky

Sníží počet silných odkazů aktuálního `WeakReference` objektu.

Pokud se počet silných odkazů změní na `nullptr`nulu, je nastaven a )

### <a name="return-value"></a>Návratová hodnota

Snížený počet silných odkazů.

## <a name="weakreferenceincrementstrongreference"></a><a name="incrementstrongreference"></a>WeakReference::IncrementStrongReference

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Návratová hodnota

Počet přírůstcích silných odkazů.

### <a name="remarks"></a>Poznámky

Zintáží silný počet odkazů `WeakReference` aktuálního objektu.

## <a name="weakreferenceresolve"></a><a name="resolve"></a>WeakReference::Vyřešit

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry

*riid řekl:*<br/>
ID rozhraní.

*ppvObjekt*<br/>
Po dokončení této operace, kopie aktuální silný odkaz, pokud je silný počet odkazů nenulová.

### <a name="return-value"></a>Návratová hodnota

- S_OK pokud je tato operace úspěšná a počet silných odkazů je nula. Parametr *ppvObject* je `nullptr`nastaven na hodnotu .

- S_OK pokud je tato operace úspěšná a počet silných odkazů je nenulová. Parametr *ppvObject* je nastaven na silný odkaz.

- V opačném případě HRESULT, který označuje důvod, proč se tato operace nezdařila.

### <a name="remarks"></a>Poznámky

Nastaví zadaný ukazatel na aktuální silnou referenční hodnotu, pokud je počet silných odkazů nenulový.

## <a name="weakreferencesetunknown"></a><a name="setunknown"></a>WeakReference::SetUnknown

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parametry

*unk*<br/>
Ukazatel na `IUnknown` rozhraní objektu.

### <a name="remarks"></a>Poznámky

Nastaví silný odkaz `WeakReference` aktuálního objektu na zadaný ukazatel rozhraní.

## <a name="weakreferenceweakreference"></a><a name="weakreference"></a>WeakReference::WeakReference

Podporuje infrastrukturu WRL a není určen pro použití přímo z vašeho kódu.

```cpp
WeakReference();
```

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy. `WeakReference`

Silný referenční ukazatel `WeakReference` pro objekt je `nullptr`inicializován na , a silný počet odkazů je inicializován na 1.
