---
title: Platform::Agile – třída
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- AGILE/Platform::Platform
- AGILE/Platform::Platform::Agile::Agile
- AGILE/Platform::Platform::Agile::Get
- AGILE/Platform::Platform::Agile::GetAddressOf
- AGILE/Platform::Platform::Agile::GetAddressOfForInOut
- AGILE/Platform::Platform::Agile::Release
helpviewer_keywords:
- Platform::Agile
ms.assetid: e34459a9-c429-4c79-97fd-030c43ca4155
ms.openlocfilehash: 0822cef10b199a5bc3b33f116065816e380bf8a8
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81376504"
---
# <a name="platformagile-class"></a>Platform::Agile – třída

Představuje objekt, který má MashalingBehavior=Standard jako agilní objekt, což výrazně snižuje pravděpodobnost pro výjimky zřetězení za běhu. Umožňuje `Agile<T>` neagilní objekt volat nebo být volány z stejné nebo jiné vlákno. Další informace naleznete v [tématu Threading and Marshaling](../cppcx/threading-and-marshaling-c-cx.md).

## <a name="syntax"></a>Syntaxe

```cpp
template <typename T>
class Agile;
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Název typu pro třídu bez agilní.

### <a name="remarks"></a>Poznámky

Většina tříd v prostředí Windows Runtime jsou agilní. Agilní objekt můžete volat nebo volat, in proc nebo out-of-proc objektu ve stejném nebo jiném vlákně. Pokud objekt není agilní, zabalte neagilní `Agile<T>` objekt v objektu, který je agilní. Potom `Agile<T>` objekt může být zařazen a základní neagilní objekt lze použít.

Třída `Agile<T>` je nativní, standardní třída C++ a vyžaduje `agile.h`. Představuje neagilní objekt a *kontext*objektu Agile . Kontext určuje model zřetězení agilního objektu a chování zařazování. Operační systém používá kontext k určení, jak zařadit objekt.

### <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Name (Název)|Popis|
|----------|-----------------|
|[Agilní::Agilní](#ctor)|Inicializuje novou instanci agilní třídy.|
|[Agilní::~Agilní destruktor](#dtor)|Zničí aktuální instanci agilní třídy.|

### <a name="public-methods"></a>Veřejné metody

|Name (Název)|Popis|
|----------|-----------------|
|[Agilní::Získat](#get)|Vrátí popisovač objektu, který je reprezentován aktuálním objektem Agile.|
|[Agilní::GetAddressOf](#getaddressof)|Znovu inicializuje aktuální agilní objekt a potom vrátí adresu popisovače `T`objektu typu .|
|[Agilní::GetAddressOfForInOut](#getaddressofforinout)|Vrátí adresu popisovače objektu reprezentovanému aktuálním objektem Agile.|
|[Agilní::Vydání](#release)|Zahodí základní objekt a kontext aktuálního objektu Agile.|

### <a name="public-operators"></a>Veřejné operátory

|Name (Název)|Popis|
|----------|-----------------|
|[Agilní::operátor->](#operator-arrow)|Načte popisovač na objekt reprezentované aktuální agilní objekt.|
|[Agilní::operátor=](#operator-assign)|Přiřadí zadanou hodnotu aktuálnímu objektu Agile.|

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`Object`

`Agile`

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Záhlaví:** agile.h

## <a name="agileagile-constructor"></a><a name="ctor"></a>Agilní::Agilní konstruktor

Inicializuje novou instanci agilní třídy.

## <a name="syntax"></a>Syntaxe

```cpp
Agile();
Agile(T^ object);
Agile(const Agile<T>& object);
Agile(Agile<T>&& object);
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ určený parametrem typename šablony.

*Objekt*<br/>
Ve druhé verzi tohoto konstruktoru objekt slouží k inicializaci nové instance Agile. Ve třetí verzi objekt, který je zkopírován do nové instance Agile. Ve čtvrté verzi objekt, který je přesunut do nové instance Agile.

### <a name="remarks"></a>Poznámky

První verze tohoto konstruktoru je výchozí konstruktor. Druhá verze inicializuje novou třídu instance Agile `object` z objektu určeného parametrem. Třetí verze je konstruktor kopie. Čtvrtá verze je konstruktor move. Tento konstruktor nemůže vyvolat výjimky.

## <a name="agileagile-destructor"></a><a name="dtor"></a>Agilní::~Agilní destruktor

Zničí aktuální instanci agilní třídy.

## <a name="syntax"></a>Syntaxe

```cpp
~Agile();
```

### <a name="remarks"></a>Poznámky

Tento destruktor také uvolní objekt reprezentované aktuální agilní objekt.

## <a name="agileget-method"></a><a name="get"></a>Agilní::Get Metoda

Vrátí popisovač objektu, který je reprezentován aktuálním objektem Agile.

## <a name="syntax"></a>Syntaxe

```cpp
T^ Get() const;
```

### <a name="return-value"></a>Návratová hodnota

Popisovač objektu, který je reprezentován aktuální magilní objekt.

Typ vrácené hodnoty je ve skutečnosti nezveřejněný vnitřní typ. Pohodlný způsob, jak podržet vrácenou hodnotu, je přiřadit ji proměnné, která je deklarována pomocí klíčového slova **automatického** odpočtu typu. Například, `auto x = myAgileTvariable->Get();`.

## <a name="agilegetaddressof-method"></a><a name="getaddressof"></a>Agile::Metoda GetAddressOf

Znovu inicializuje aktuální agilní objekt a potom vrátí adresu popisovače `T`objektu typu .

## <a name="syntax"></a>Syntaxe

```cpp
T^* GetAddressOf() throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ určený parametrem typename šablony.

### <a name="return-value"></a>Návratová hodnota

Adresa popisovače objektu typu `T`.

### <a name="remarks"></a>Poznámky

Tato operace uvolní aktuální reprezentaci `T`objektu typu , pokud existuje; znovu inicializuje datové členy objektu Agile; získá aktuální kontext threadingu; a potom vrátí adresu proměnné handle-to-object, která může představovat neagilní objekt. Chcete-li, aby instance třídy Agile představovala objekt,[přiřaďte](#operator-assign)objekt instanci třídy Agile pomocí operátoru přiřazení objektu.

## <a name="agilegetaddressofforinout-method"></a><a name="getaddressofforinout"></a>Agilní::Metoda GetAddressOfForInOut

Vrátí adresu popisovače objektu reprezentovanému aktuálním objektem Agile.

## <a name="syntax"></a>Syntaxe

```cpp
T^* GetAddressOfForInOut()  throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ určený parametrem typename šablony.

### <a name="return-value"></a>Návratová hodnota

Adresa popisovače objektu reprezentovaného aktuálním objektem Agile.

### <a name="remarks"></a>Poznámky

Tato operace získá aktuální kontext zřetězení a potom vrátí adresu popisovače podkladovému objektu.

## <a name="agilerelease-method"></a><a name="release"></a>Agilní::Metoda vydání

Zahodí základní objekt a kontext aktuálního objektu Agile.

## <a name="syntax"></a>Syntaxe

```cpp
void Release() throw();
```

### <a name="remarks"></a>Poznámky

Základní objekt a kontext aktuálního objektu Agile jsou zahozeny, pokud existují, a pak je hodnota objektu Agile nastavena na hodnotu null.

## <a name="agileoperator-gt-operator"></a><a name="operator-arrow"></a>Agilní::Operátor-&gt; Operátor

Načte popisovač na objekt reprezentované aktuální agilní objekt.

## <a name="syntax"></a>Syntaxe

```cpp
T^ operator->() const throw();
```

### <a name="return-value"></a>Návratová hodnota

Úchyt k objektu reprezentovanéaktuální agilní objekt.

Tento operátor ve skutečnosti vrátí nezveřejněný vnitřní typ. Pohodlný způsob, jak podržet vrácenou hodnotu, je přiřadit ji proměnné, která je deklarována pomocí klíčového slova **automatického** odpočtu typu.

## <a name="agileoperator-operator"></a><a name="operator-assign"></a>Agilní::operátor= Operátor

Přiřadí zadaný objekt aktuálnímu objektu Agile.

## <a name="syntax"></a>Syntaxe

```cpp
Agile<T> operator=( T^ object ) throw();
Agile<T> operator=( const Agile<T>& object ) throw();
Agile<T> operator=( Agile<T>&& object ) throw();
T^ operator=( IUnknown* lp ) throw();
```

#### <a name="parameters"></a>Parametry

*T*<br/>
Typ určený typename šablony.

*Objekt*<br/>
Objekt nebo popisovač objektu, který je zkopírován nebo přesunut do aktuálního objektu Agile.

*Lp*<br/>
Ukazatel rozhraní IUnknown objektu.

### <a name="return-value"></a>Návratová hodnota

Úchyt k objektu typu`T`

### <a name="remarks"></a>Poznámky

První verze operátoru přiřazení zkopíruje popisovač do typu odkazu na aktuální agilní objekt. Druhá verze zkopíruje odkaz na agilní typ na aktuální agilní objekt. Třetí verze přesune agilní typ na aktuální agilní objekt. Čtvrtá verze přesune ukazatel na objekt COM na aktuální agilní objekt.

Operace přiřazení automaticky zachová kontext aktuálního objektu Agile.

## <a name="see-also"></a>Viz také

[Obor názvů platformy](platform-namespace-c-cx.md)
