---
title: filesystem_error – třída
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: 7bd6b2d3d716ba25999388d44e7bd5a8d0750eb5
ms.sourcegitcommit: 76cc69b482ada8ebf0837e8cdfd4459661f996dd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71127203"
---
# <a name="filesystem_error-class"></a>filesystem_error – třída

Základní třída pro všechny výjimky, které jsou vyvolány k hlášení přetečení systému nízké úrovně.

## <a name="syntax"></a>Syntaxe

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Poznámky

Třída slouží jako základní třída pro všechny výjimky vyvolané k nahlášení chyby ve \<funkcích systému souborů >. Ukládá objekt typu `string`, který je zde volán `mymesg` pro účely Exposition. Také ukládá dva objekty typu `path`s názvem `mypval1` a `mypval2`.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[filesystem_error](#filesystem_error)|`filesystem_error` Vytvoří zprávu.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[path1](#path1)|Vrátí`mypval1`|
|[path2](#path2)|Vrátí`mypval2`|
|[Co](#what)|Vrátí ukazatel na `NTBS`.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> systému souborů

**Obor názvů:** std:: experimentální:: FileSystem

## <a name="filesystem_error"></a>filesystem_error

První konstruktor vytvoří svou zprávu z *what_arg* a *ES*. Druhý konstruktor také vytvoří svou zprávu z *Pval1*, která je uložena v `mypval1`. Třetí konstruktor také vytvoří svou zprávu z *Pval1*, kterou ukládá v `mypval1`a z *Pval2*, které ukládá v `mypval2`.

```cpp
filesystem_error(const string& what_arg,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    error_code ec);

filesystem_error(const string& what_arg,
    const path& pval1,
    const path& pval2,
    error_code ec);
```

### <a name="parameters"></a>Parametry

*what_arg*\
Zadaná zpráva

*EHS*\
Zadaný kód chyby

*mypval1*\
Další zadaný parametr zprávy

*mypval2*\
Další zadaný parametr zprávy

## <a name="path1"></a>path1

Členská funkce vrátí`mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a>path2

Členská funkce vrátí`mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a>Co

`NTBS`Členská funkce vrátí ukazatel na objekt, který je nejlépe složený z `system_error::what()` `runtime_error::what()`, `mymesg`, `mypval1.native_string()`, a `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```
