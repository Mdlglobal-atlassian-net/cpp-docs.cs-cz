---
title: Platforma::Třída výjimek
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::Exception::Exception
- VCCORLIB/Platform::Exception::CreateException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::Exception Class
ms.assetid: ca1d5a67-3a5a-48fe-8099-f9c38a2d2dce
ms.openlocfilehash: 4604769d9d1bc5fa848d15459327dc87d82f7016
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/14/2020
ms.locfileid: "81363773"
---
# <a name="platformexception-class"></a>Platforma::Třída výjimek

Představuje chyby, ke kterým dochází během provádění aplikace. Vlastní třídy výjimek nelze `Platform::Exception`odvodit z . Pokud požadujete vlastní výjimku, `Platform::COMException` můžete použít a zadat HRESULT specifické pro aplikaci.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class Exception : Object,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Členové

Třída `Exception` dědí z `Object` třídy `IException` `IPrintable`a `IEquatable` , a rozhraní.

Třída `Exception` má také následující druhy členů.

### <a name="constructors"></a>Konstruktory

|Člen|Popis|
|------------|-----------------|
|[Výjimka::Výjimka](#ctor)|Inicializuje novou instanci třídy. `Exception`|

### <a name="methods"></a>Metody

Třída `Exception` dědí `Equals()`, `Finalize()``GetHashCode()`,`GetType()``MemberwiseClose()`, `ToString()` a metody z [Platform::Object Class](../cppcx/platform-object-class.md). Třída `Exception` má také následující metodu.

|Člen|Popis|
|------------|-----------------|
|[Výjimka::Vytvořitvýjimku](#createexception)|Vytvoří výjimku, která představuje zadanou hodnotu HRESULT.|

### <a name="properties"></a>Vlastnosti

Třída Exception má také následující vlastnosti.

|Člen|Popis|
|------------|-----------------|
|[Výjimka::HVýsledek](#hresult)|HRESULT, který odpovídá výjimce.|
|[Výjimka::Zpráva](#message)|Zpráva popisující výjimku Tato hodnota je jen pro čtení `Exception` a nelze ji po vytvoření vytvořit.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný server:** Windows Server 2012

**Obor názvů:** Platforma

**Metadata:** platform.winmd

## <a name="exceptioncreateexception-method"></a><a name="createexception"></a>Výjimka::Metoda CreateException

Vytvoří platformu::Exception^ ze zadané hodnoty HRESULT.

### <a name="syntax"></a>Syntaxe

```cpp
Exception^ CreateException(int32 hr);
Exception^ CreateException(int32 hr, Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*Hr*<br/>
Hodnota HRESULT, kterou obvykle získáte z volání metody COM. Pokud je hodnota 0, která se rovná S_OK, tato metoda vyvolá [Platform::InvalidArgumentException](../cppcx/platform-invalidargumentexception-class.md) protože metody COM, které jsou úspěšné, by neměly vyvolávat výjimky.

*Zprávu*<br/>
Řetězec, který popisuje chybu.

### <a name="return-value"></a>Návratová hodnota

Výjimka, která představuje chybu HRESULT.

### <a name="remarks"></a>Poznámky

Pomocí této metody můžete vytvořit výjimku z HRESULT, která je vrácena například z volání metody rozhraní COM. Můžete použít přetížení, které trvá String^ parametr poskytnout vlastní zprávu.

Důrazně doporučujeme použít CreateException k vytvoření výjimky silného typu, nikoli k vytvoření [platformy::COMException,](../cppcx/platform-comexception-class.md) která obsahuje pouze HRESULT.

## <a name="exceptionexception-constructor"></a><a name="ctor"></a>Výjimka::Konstruktor výjimek

Intializes novou instanci Exception třídy.

### <a name="syntax"></a>Syntaxe

```cpp
Exception(int32 hresult);
Exception(int32 hresult, ::Platform::String^ message);
```

### <a name="parameters"></a>Parametry

*Hresult*<br/>
Chyba HRESULT, která je reprezentována výjimkou.

*Zprávu*<br/>
Zpráva zadaná uživatelem, například normativní text, která je přidružena k výjimce. Obecně byste měli dát přednost druhé přetížení za účelem poskytnutí popisné zprávy, která je co nejkonkrétnější o tom, jak a proč došlo k chybě.

## <a name="exceptionhresult-property"></a><a name="hresult"></a>Výjimka::Vlastnost HResult

HRESULT, který odpovídá výjimce.

### <a name="syntax"></a>Syntaxe

```cpp
public:
    property int HResult { int get(); }
```

## <a name="property-value"></a>Hodnota vlastnosti

Hodnota HRESULT.

### <a name="remarks"></a>Poznámky

Většina výjimek začíná jako chyby COM, které jsou vráceny jako hodnoty HRESULT. C++/CX převede tyto hodnoty na objekty Platform::Exception^ a tato vlastnost ukládá hodnotu původního kódu chyby.

## <a name="exceptionmessage-property"></a><a name="message"></a>Výjimka::Vlastnost Zprávy

Zpráva, která popisuje chybu.

### <a name="syntax"></a>Syntaxe

```cpp
public:property String^ Message;
```

## <a name="property-value"></a>Hodnota vlastnosti

Ve výjimečných výjimkách, které pocházejí z prostředí Windows Runtime, se jedná o systémově zadaný popis chyby.

### <a name="remarks"></a>Poznámky

V systému Windows 8 je tato vlastnost jen pro čtení, protože výjimky v této verzi prostředí Windows Runtime jsou přenášeny přes ABI pouze jako HRESULTS. Ve Windows 8.1 bohatší informace o výjimce jsou přenášeny přes ABI a můžete poskytnout vlastní zprávu, že ostatní součásti přístup programově. Další informace naleznete v [tématu Výjimky (C++/CX)](../cppcx/exceptions-c-cx.md).

## <a name="see-also"></a>Viz také

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
