---
title: 'Platform:: COMException – třída'
ms.date: 12/30/2016
ms.topic: reference
f1_keywords:
- VCCORLIB/Platform::COMException
- VCCORLIB/Platform::Exception::HResult
- VCCORLIB/Platform::Exception::Message
helpviewer_keywords:
- Platform::COMException Class
ms.assetid: 44fda4e5-574f-4d12-ab5f-4ff3f277448d
ms.openlocfilehash: eb6f3e0e4860687d0d47294e11b7741294abac20
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/15/2019
ms.locfileid: "69500551"
---
# <a name="platformcomexception-class"></a>Platform:: COMException – třída

Představuje chyby modelu COM, ke kterým dochází při provádění aplikace. COMException je základní třída pro sadu předdefinovaných standardních výjimek.

## <a name="syntax"></a>Syntaxe

```cpp
public ref class COMException : Exception,    IException,    IPrintable,    IEquatable
```

### <a name="members"></a>Členové

Třída COMException dědí z třídy Object a rozhraní IException, IPrintable a IEquatable.

COMException má také následující typy členů.

**Konstruktory**

|Člen|Popis|
|------------|-----------------|
|[COMException](#ctor)|Inicializuje novou instanci třídy COMException.|

**Metody**

Třída COMException dědí metody Equals (), Finalize (), GetHashCode (), GetType (), MemberwiseClose () a ToString () z [třídy Platform:: Object](../cppcx/platform-object-class.md).

**Vlastnosti**

Třída COMException má následující vlastnosti.

|Člen|Popis|
|------------|-----------------|
|[Výjimka:: HResult](#hresult)|Hodnota HRESULT, která odpovídá výjimce.|
|[Výjimka:: zpráva](#message)|Zpráva popisující výjimku.|

## <a name="derived-exceptions"></a>Odvozené výjimky

Následující předdefinované výjimky jsou odvozeny z COMException. Liší se od COMException pouze v jejich názvu, názvu svého konstruktoru a jejich podkladové hodnotě HRESULT.

|Name|Základní HRESULT|Popis|
|----------|------------------------|-----------------|
|COMException|*uživatelem definovaná hodnota HRESULT*|Vyvolána, pokud se vrátí nerozpoznaný HRESULT z volání metody modelu COM.|
|AccessDeniedException|E_ACCESSDENIED|Vyvoláno, když je odepřen přístup k prostředku nebo funkci.|
|ChangedStateException|E_CHANGED_STATE|Vyvoláno, když jsou volány metody iterátoru kolekce nebo zobrazení kolekce po změně nadřazené kolekce, což způsobí zrušení platnosti výsledků metody.|
|ClassNotRegisteredException|REGDB_E_CLASSNOTREG|Vyvoláno, když nebyla zaregistrována třída COM.|
|DisconnectedException|RPC_E_DISCONNECTED|Vyvoláno, když je objekt odpojen od klientů.|
|FailureException|E_FAIL|Vyvoláno, když dojde k chybě operace.|
|InvalidArgumentException|E_INVALIDARG|Vyvolána, pokud jeden z argumentů poskytnutý metodě není platný.|
|InvalidCastException|E_NOINTERFACE|Vyvoláno, když typ nelze přetypovat na jiný typ.|
|NotImplementedException|E_NOTIMPL|Vyvoláno, pokud metoda rozhraní nebyla pro třídu implementována.|
|NullReferenceException|E_POINTER|Vyvolána, když dojde k pokusu o zpětnou odkazování na nulový odkaz na objekt.|
|OperationCanceledException|E_ABORT|Vyvolána, když je operace přerušena.|
|OutOfBoundsException|E_BOUNDS|Vyvolá se, když se operace pokusí o přístup k datům mimo platný rozsah.|
|OutOfMemoryException|E_OUTOFMEMORY|Vyvoláno, pokud k dokončení operace není dostatek paměti.|

### <a name="requirements"></a>Požadavky

**Minimální podporovaný klient:** Windows 8

**Minimální podporovaný Server:** Windows Server 2012

**Hosting** Platforma

**Metadata:** Platform. winmd

## <a name="ctor"></a>COMException:: COMException – konstruktor

Inicializuje novou instanci třídy COMException.

### <a name="syntax"></a>Syntaxe

```cpp
COMException( int hresult )
```

### <a name="parameters"></a>Parametry

*HRESULT*<br/>
Chyba HRESULT, která je reprezentovaná výjimkou.

## <a name="hresult"></a>COMException:: HResult – vlastnost

Hodnota HRESULT, která odpovídá výjimce.

### <a name="syntax"></a>Syntaxe

```cpp
public:
    property int HResult { int get();}
```

## <a name="property-value"></a>Hodnota vlastnosti

Hodnota HRESULT, která určuje chybu.

### <a name="remarks"></a>Poznámky

Další informace o tom, jak interpretovat hodnotu HRESULT, najdete v tématu [Struktura chybových kódů modelu COM](/windows/win32/com/structure-of-com-error-codes).

## <a name="message"></a>COMException:: Message – vlastnost

Zpráva popisující výjimku.

### <a name="syntax"></a>Syntaxe

```cpp
public:property String^ Message {    String^ get();}
```

### <a name="property-value"></a>Hodnota vlastnosti

Popis výjimky

## <a name="see-also"></a>Viz také:

[Platform – obor názvů](../cppcx/platform-namespace-c-cx.md)
