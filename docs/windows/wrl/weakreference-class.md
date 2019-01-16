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
ms.openlocfilehash: a3372a176a158dd9c89eb888c8deb0244eef9a84
ms.sourcegitcommit: 360b55e89e5954f494e52b1cf989fbaceda06f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/16/2019
ms.locfileid: "54334738"
---
# <a name="weakreference-class"></a>WeakReference – třída

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

## <a name="syntax"></a>Syntaxe

```cpp
class WeakReference;
```

## <a name="remarks"></a>Poznámky

Představuje *nestálý odkaz* , který je možné pomocí prostředí Windows Runtime nebo klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.

A `WeakReference` udržuje objekt *silného odkazu*, což je ukazatel na objekt a *silného odkazu počet*, což je počet kopií silného odkazu, který byl distribuován podle `Resolve()` metody. Počet silného odkazu je nenulová, silný odkaz je platný a je přístupný objekt. Když počet odkazů silné klesne na nulu, silný odkaz je neplatný a objekt je nedostupný.

A `WeakReference` objekt se obvykle používá k reprezentaci objektu, jehož existence je řízena vnějším vláknem nebo aplikací. Například sestavit `WeakReference` objekt z odkazu na objekt souboru. Když je soubor otevřen, silný odkaz je platný. Ale pokud se soubor zavře, silný odkaz níže uvedených situací.

`WeakReference` Metody jsou bezpečné pro vlákna.

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

Název                                                  | Popis
----------------------------------------------------- | ---------------------------------------------------------------------------
[Weakreference::weakreference –](#weakreference)        | Inicializuje novou instanci třídy `WeakReference` třídy.
[WeakReference:: ~ weakreference –](#tilde-weakreference) | Zruší inicializaci (odstraní) aktuální instancí třídy `WeakReference` třídy.

### <a name="public-methods"></a>Veřejné metody

Název                                                                 | Popis
-------------------------------------------------------------------- | ----------------------------------------------------------------------------------------------------------
[WeakReference::DecrementStrongReference](#decrementstrongreference) | Sníží počet silné referenční aktuálního `WeakReference` objektu.
[Weakreference::incrementstrongreference –](#incrementstrongreference) | Zvýší počet odkazů silné aktuálního `WeakReference` objektu.
[Weakreference::Resolve –](#resolve)                                   | Nastaví zadaný ukazatel na aktuální hodnotu silného odkazu, pokud je počet odkazů silné nenulové.
[Weakreference::setunknown –](#setunknown)                             | Nastaví silný odkaz aktuální `WeakReference` objektu na zadané rozhraní ukazatel.

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`WeakReference`

## <a name="requirements"></a>Požadavky

**Záhlaví:** implements.h

**Namespace:** Microsoft::WRL::Details

## <a name="tilde-weakreference"></a>WeakReference:: ~ weakreference –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
virtual ~WeakReference();
```

### <a name="return-value"></a>Návratová hodnota

### <a name="remarks"></a>Poznámky

Zruší inicializaci aktuální instance `WeakReference` třídy.

## <a name="decrementstrongreference"></a>WeakReference::DecrementStrongReference

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
ULONG DecrementStrongReference();
```

### <a name="remarks"></a>Poznámky

Sníží počet silné referenční aktuálního `WeakReference` objektu.

Když počet odkazů silné klesne na nulu, silného odkazu se nastaví na `nullptr`.

### <a name="return-value"></a>Návratová hodnota

Počet odkazů sníží silné.

## <a name="incrementstrongreference"></a>Weakreference::incrementstrongreference –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
ULONG IncrementStrongReference();
```

### <a name="return-value"></a>Návratová hodnota

Počet zvýšena silného odkazu.

### <a name="remarks"></a>Poznámky

Zvýší počet odkazů silné aktuálního `WeakReference` objektu.

## <a name="resolve"></a>Weakreference::Resolve –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
STDMETHOD(Resolve)
   (REFIID riid,
   _Deref_out_opt_ IInspectable **ppvObject
);
```

### <a name="parameters"></a>Parametry

*riid*<br/>
Identifikátor rozhraní.

*ppvObject*<br/>
Když tato operace dokončí, kopii aktuální silného odkazu, pokud je počet odkazů silné nenulové.

### <a name="return-value"></a>Návratová hodnota

- S_OK, pokud je tato operace úspěšná, a počet silného odkazu je nula. *PpvObject* parametr je nastaven na `nullptr`.

- S_OK, pokud je tato operace úspěšná a počet silného odkazu není nenulová. *PpvObject* parametr je nastaven na silný odkaz.

- V opačném případě HRESULT, který označuje důvod tato operace se nezdařila.

### <a name="remarks"></a>Poznámky

Nastaví zadaný ukazatel na aktuální hodnotu silného odkazu, pokud je počet odkazů silné nenulové.

## <a name="setunknown"></a>Weakreference::setunknown –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
void SetUnknown(
   _In_ IUnknown* unk
);
```

### <a name="parameters"></a>Parametry

*UNK*<br/>
Ukazatel `IUnknown` rozhraní objektu.

### <a name="remarks"></a>Poznámky

Nastaví silný odkaz aktuální `WeakReference` objektu na zadané rozhraní ukazatel.

## <a name="weakreference"></a>Weakreference::weakreference –

Podporuje knihovny WRL infrastrukturu a není určena pro použití přímo v kódu.

```cpp
WeakReference();
```

### <a name="remarks"></a>Poznámky

Inicializuje novou instanci třídy `WeakReference` třídy.

Ukazatele silného odkazu `WeakReference` objekt je inicializován na `nullptr`, a počet silného odkazu je inicializován na hodnotu 1.
