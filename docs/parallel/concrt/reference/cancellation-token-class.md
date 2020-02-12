---
title: cancellation_token – třída
ms.date: 11/04/2016
f1_keywords:
- cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::cancellation_token
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::deregister_callback
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_cancelable
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::is_canceled
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::none
- PPLCANCELLATION_TOKEN/concurrency::cancellation_token::register_callback
helpviewer_keywords:
- cancellation_token class
ms.assetid: 2787df2b-e9d3-440e-bfd0-841a46a9835f
ms.openlocfilehash: 34743ce48510eec9d8f7862e5ed951a722932962
ms.sourcegitcommit: a8ef52ff4a4944a1a257bdaba1a3331607fb8d0f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77142250"
---
# <a name="cancellation_token-class"></a>cancellation_token – třída

Třída `cancellation_token` představuje možnost určit, zda některé operace byly vyžádány pro zrušení. Daný token lze přidružit k `task_group`, `structured_task_group`nebo `task` k poskytnutí implicitního zrušení. Může být také dotazování na zrušení nebo zaregistrováno zpětné volání pro IF a při zrušení přidruženého `cancellation_token_source`.

## <a name="syntax"></a>Syntaxe

```cpp
class cancellation_token;
```

## <a name="members"></a>Členové

### <a name="public-constructors"></a>Veřejné konstruktory

|Název|Popis|
|----------|-----------------|
|[cancellation_token](#ctor)||
|[~ cancellation_token destruktor](#dtor)||

### <a name="public-methods"></a>Veřejné metody

|Název|Popis|
|----------|-----------------|
|[deregister_callback](#deregister_callback)|Odstraní zpětné volání, které bylo dříve registrováno prostřednictvím metody `register` na základě `cancellation_token_registration` objektu vráceného v době registrace.|
|[is_cancelable](#is_cancelable)|Vrátí informaci o tom, zda tento token může být zrušen nebo nikoli.|
|[is_canceled](#is_canceled)|Vrátí **hodnotu true** , pokud byl token zrušen.|
|[nTato](#none)|Vrátí token zrušení, který nemůže být nikdy předmětem zrušení.|
|[register_callback](#register_callback)|Zaregistruje funkci zpětného volání s tokenem. Pokud a při zrušení tokenu, bude provedeno zpětné volání. Všimněte si, že pokud je token již zrušen v místě, kde je tato metoda volána, zpětné volání bude provedeno okamžitě a synchronně.|

### <a name="public-operators"></a>Veřejné operátory

|Název|Popis|
|----------|-----------------|
|[operator!=](#operator_neq)||
|[operátor =](#operator_eq)||
|[operator = = – operátor](#operator_eq_eq)||

## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti

`cancellation_token`

## <a name="requirements"></a>Požadavky

**Záhlaví:** pplcancellation_token. h

**Obor názvů:** souběžnost

## <a name="dtor"></a>~ cancellation_token

```cpp
~cancellation_token();
```

## <a name="ctor"></a>cancellation_token

```cpp
cancellation_token(const cancellation_token& _Src);

cancellation_token(cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
Cancellation_token ke zkopírování nebo přesunutí.

## <a name="deregister_callback"></a>deregister_callback

Odstraní zpětné volání, které bylo dříve registrováno prostřednictvím metody `register` na základě `cancellation_token_registration` objektu vráceného v době registrace.

```cpp
void deregister_callback(const cancellation_token_registration& _Registration) const;
```

### <a name="parameters"></a>Parametry

*_Registration*<br/>
Objekt `cancellation_token_registration` odpovídající zpětnému volání, které má být odregistrováno. Tento token musí být dříve vrácen z volání metody `register`.

## <a name="is_cancelable"></a>is_cancelable

Vrátí informaci o tom, zda tento token může být zrušen nebo nikoli.

```cpp
bool is_cancelable() const;
```

### <a name="return-value"></a>Návratová hodnota

Označení, zda tento token může být zrušen nebo nikoli.

## <a name="is_canceled"></a>is_canceled

Vrátí **hodnotu true** , pokud byl token zrušen.

```cpp
bool is_canceled() const;
```

### <a name="return-value"></a>Návratová hodnota

Hodnota **true** , pokud byl token zrušen; v opačném případě hodnota **false**.

## <a name="none"></a>nTato

Vrátí token zrušení, který nemůže být nikdy předmětem zrušení.

```cpp
static cancellation_token none();
```

### <a name="return-value"></a>Návratová hodnota

Token zrušení, který nelze zrušit.

## <a name="operator_neq"></a>! = – operátor

```cpp
bool operator!= (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` k porovnání.

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_eq"></a>operátor =

```cpp
cancellation_token& operator= (const cancellation_token& _Src);

cancellation_token& operator= (cancellation_token&& _Src);
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` k přiřazení.

### <a name="return-value"></a>Návratová hodnota

## <a name="operator_eq_eq"></a>operator = = – operátor

```cpp
bool operator== (const cancellation_token& _Src) const;
```

### <a name="parameters"></a>Parametry

*_Src*<br/>
`cancellation_token` k porovnání.

### <a name="return-value"></a>Návratová hodnota

## <a name="register_callback"></a>register_callback

Zaregistruje funkci zpětného volání s tokenem. Pokud a při zrušení tokenu, bude provedeno zpětné volání. Všimněte si, že pokud je token již zrušen v místě, kde je tato metoda volána, zpětné volání bude provedeno okamžitě a synchronně.

```cpp
template<typename _Function>
::Concurrency::cancellation_token_registration register_callback(const _Function& _Func) const;
```

### <a name="parameters"></a>Parametry

*_Function*<br/>
Typ objektu funkce, který bude volán zpět při zrušení tohoto `cancellation_token`.

*_Func*<br/>
Objekt funkce, který bude volán zpět při zrušení tohoto `cancellation_token`.

### <a name="return-value"></a>Návratová hodnota

Objekt `cancellation_token_registration`, který může být využíván v metodě `deregister` pro zrušení registrace dříve zaregistrovaného zpětného volání a zabránění jeho provedení. Metoda vyvolá výjimku [invalid_operation](invalid-operation-class.md) , pokud je volána na objektu `cancellation_token`, který byl vytvořen pomocí metody [cancellation_token:: none](#none) .

## <a name="see-also"></a>Viz také

[concurrency – obor názvů](concurrency-namespace.md)
