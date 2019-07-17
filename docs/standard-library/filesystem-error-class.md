---
title: filesystem_error – třída
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::filesystem_error
ms.assetid: c53aac27-c1fa-43e4-8967-48ea8ba1f172
ms.openlocfilehash: c3dbfc080f0a1494950016f42189d932be05b0f1
ms.sourcegitcommit: 3590dc146525807500c0477d6c9c17a4a8a2d658
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/16/2019
ms.locfileid: "68240732"
---
# <a name="filesystemerror-class"></a>filesystem_error – třída

Základní třída pro všechny výjimky, které jsou vyvolány hlášení nižší úrovně systému přetečení.

## <a name="syntax"></a>Syntaxe

```cpp
class filesystem_error    : public system_error;
```

## <a name="remarks"></a>Poznámky

Tato třída slouží jako základní třída pro všechny výjimky vyvolané oznámit chybu v \<filesystem > funkce. Uloží objekt typu `string`, označované jako `mymesg` zde pro účely budeme. Také ukládá dva objekty typu `path`, označované jako `mypval1` a `mypval2`.

## <a name="members"></a>Členové

### <a name="constructors"></a>Konstruktory

|||
|-|-|
|[filesystem_error](#filesystem_error)|Vytvoří `filesystem_error` zprávy.|

### <a name="functions"></a>Funkce

|||
|-|-|
|[path1](#path1)|Vrátí `mypval1`|
|[cesta2](#path2)|Vrátí `mypval2`|
|[Co](#what)|Vrací ukazatel na `NTBS`.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::experimental::filesystem

## <a name="filesystem_error"></a> filesystem_error –

První konstruktor vytvoří její zprávy z *what_arg* a *ES*. Druhý konstruktor vytvoří také její zprávy z *pval1*, který je uložený v `mypval1`. Třetí konstruktor vytvoří také její zprávy z *pval1*, který je uložený v `mypval1`a z *pval2*, který je uložený v `mypval2`.

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
Zadaná zpráva.

*ES*\
Zadaný kód chyby.

*mypval1*\
Další parametr zadané zprávy.

*mypval2*\
Další zadané býváte parametr.

## <a name="path1"></a> cesta1

Členská funkce vrátí `mypval1`

```cpp
const path& path1() const noexcept;
```

## <a name="path2"></a> cesta2

Členská funkce vrátí `mypval2`

```cpp
const path& path2() const noexcept;
```

## <a name="what"></a> Co

Členská funkce vrátí ukazatel `NTBS`, pokud možno skládá z `runtime_error::what()`, `system_error::what()`, `mymesg`, `mypval1.native_string()`, a `mypval2.native_string()`.

```cpp
const char *what() const noexcept;
```
