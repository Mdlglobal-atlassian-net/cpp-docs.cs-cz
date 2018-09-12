---
title: file_status – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 09/10/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- filesystem/std::experimental::filesystem::file_status
- filesystem/std::experimental::filesystem::file_status::operator=
- filesystem/std::experimental::filesystem::file_status::type
- filesystem/std::experimental::filesystem::file_status::permissions
dev_langs:
- C++
ms.assetid: 9781840e-ad22-44dd-ad79-0fabaa94bac4
author: corob-msft
ms.author: corob
helpviewer_keywords:
- std::experimental::filesystem::file_status
- std::experimental::filesystem::file_status::operator=
- std::experimental::filesystem::file_status::type
- std::experimental::filesystem::file_status::permissions
ms.workload:
- cplusplus
ms.openlocfilehash: cc45e785b6a3aeefd9e2cf5d0539b5d387af7143
ms.sourcegitcommit: fb9448eb96c6351a77df04af16ec5c0fb9457d9e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44691663"
---
# <a name="filestatus-class"></a>file_status – třída

Zabalí [file_type](../standard-library/filesystem-enumerations.md#file_type) a soubor [oprávnění](../standard-library/filesystem-enumerations.md#perms).

## <a name="syntax"></a>Syntaxe

```cpp
class file_status;
```

### <a name="constructors"></a>Konstruktory

|Konstruktor|Popis|
|-|-|
|[file_status –](#file_status)|Vytvoří obálku pro [file_type](../standard-library/filesystem-enumerations.md#file_type) a soubor [oprávnění](../standard-library/filesystem-enumerations.md#perms).|

### <a name="member-functions"></a>Členské funkce

|Členská funkce|Popis|
|-|-|
|[Typ](#type)|Získá nebo nastaví `file_type`.|
|[Oprávnění](#permissions)|Získá nebo nastaví oprávnění k souboru.|

### <a name="operators"></a>Operátory

|Operátor|Popis|
|-|-|
|[operátor =](#op_as)|Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.|

## <a name="requirements"></a>Požadavky

**Záhlaví:** \<filesystem >

**Namespace:** std::experimental::filesystem, std::experimental::filesystem

## <a name="file_status"></a> file_status::file_status –

Vytvoří obálku pro [file_type](../standard-library/filesystem-enumerations.md#file_type) a soubor [oprávnění](../standard-library/filesystem-enumerations.md#perms).

```cpp
explicit file_status(
   file_type ftype = file_type::none,
   perms mask = perms::unknown) noexcept;

file_status(const file_status&) noexcept = default;

file_status(file_status&&) noexcept = default;

~file_status() noexcept = default;
```

### <a name="parameters"></a>Parametry

*ftype*<br/>
Zadaný `file_type`, výchozí hodnota je `file_type::none`.

*Maska*<br/>
Zadaný soubor `perms`, výchozí hodnota je `perms::unknown`.

*file_status –*<br/>
Uložený objekt.

## <a name="op_as"></a> file_status::Operator =

Operátory přiřazení nastavený na výchozí hodnotu člena chovat dle očekávání.

```cpp
file_status& operator=(const file_status&) noexcept = default;
file_status& operator=(file_status&&) nexcept = default;
```

### <a name="parameters"></a>Parametry

*file_status –*<br/>
[File_status –](../standard-library/file-status-class.md) kopírovaná do `file_status`.

## <a name="type"></a> Typ

Získá nebo nastaví `file_type`.

```cpp
file_type type() const noexcept
void type(file_type ftype) noexcept
```

### <a name="parameters"></a>Parametry

*ftype*<br/>
Zadaný `file_type`.

## <a name="permissions"></a> Oprávnění

Získá nebo nastaví oprávnění k souboru.

Můžete vytvořit soubor setter `readonly` nebo odebrat `readonly` atribut.

```cpp
perms permissions() const noexcept
void permissions(perms mask) noexcept
```

### <a name="parameters"></a>Parametry

*Maska*<br/>
Zadaný `perms`.

## <a name="see-also"></a>Viz také:

[Odkaz na soubory hlaviček](../standard-library/cpp-standard-library-header-files.md)<br/>
[path – třída](../standard-library/path-class.md)<br/>
[\<FileSystem >](../standard-library/filesystem.md)<br/>
