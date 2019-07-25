---
title: file_status – třída
ms.date: 09/10/2018
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.openlocfilehash: 60ced1f60c811f585928f47c6cfd5e695d0c4085
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2019
ms.locfileid: "68457755"
---
# <a name="filestatus-class"></a>file_status – třída

Zabalí [file_type](../standard-library/filesystem-enumerations.md#file_type) a File [permes](../standard-library/filesystem-enumerations.md#perms).

## <a name="syntax"></a>Syntaxe

```cpp
class file_status;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[file_status](#file_status)|Vytvoří obálku pro [file_type](../standard-library/filesystem-enumerations.md#file_type) a File [permes](../standard-library/filesystem-enumerations.md#perms).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[type](#type)|Získá nebo nastaví `file_type`.|
|[oprávnění](#permissions)|Získá nebo nastaví oprávnění pro soubor.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)|Výchozí operátory přiřazení členů se chovají podle očekávání.|

## <a name="requirements"></a>Požadavky

**Hlavička:** \<> systému souborů

**Obor názvů:** std:: experimentální:: FileSystem, std:: experimentální:: FileSystem

## <a name="file_status"></a>file_status::file_status

Vytvoří obálku pro [file_type](../standard-library/filesystem-enumerations.md#file_type) a File [permes](../standard-library/filesystem-enumerations.md#perms).

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Parametry

*ftype*\
Zadáno `file_type` ,`file_type::none`výchozí hodnota je.

*zrušit*\
Zadaný soubor `perms`je ve výchozím `perms::unknown`nastavení nastaven na hodnotu.

*file_status*\
Uložený objekt.

## <a name="op_as"></a>file_status:: operator =

Výchozí operátory přiřazení členů se chovají podle očekávání.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Parametry

*file_status*\
[File_status](../standard-library/file-status-class.md) , který se kopíruje `file_status`do.

## <a name="type"></a>textový

Získá nebo nastaví `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Parametry

*ftype*\
Zadáno `file_type`.

## <a name="permissions"></a>nastaven

Získá nebo nastaví oprávnění pro soubor.

Použijte metodu Setter k vytvoření souboru `readonly` nebo `readonly` odebrání atributu.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Parametry

*zrušit*\
Zadáno `perms`.

## <a name="see-also"></a>Viz také:

[Odkazy na hlavičkové soubory](../standard-library/cpp-standard-library-header-files.md)\
[path – třída](../standard-library/path-class.md)\
[\<> systému souborů](../standard-library/filesystem.md)
