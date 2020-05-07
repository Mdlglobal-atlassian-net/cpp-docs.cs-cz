---
title: Specifikátory třídy úložiště s deklaracemi funkce
ms.date: 11/04/2016
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
ms.openlocfilehash: 69d6fa2b17523f2bb4068cd05a11265d91750021
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62157876"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Specifikátory třídy úložiště s deklaracemi funkce

V deklaracích funkcí můžete **static** použít buď specifikátor `extern` třídy úložiště static, nebo. Funkce mají vždy globální životnost.

**Specifické pro Microsoft**

Deklarace funkce na vnitřní úrovni mají stejný význam jako deklarace funkce na vnější úrovni. To znamená, že funkce je viditelná z místa deklarace ve zbytku jednotky překladu i v případě, že je deklarována v místním oboru.

**Specifické pro konec Microsoftu**

Pravidla viditelnosti pro funkce se mírně liší od pravidel pro proměnné, a to takto:

- Funkce deklarovaná jako **statická** je viditelná pouze v rámci zdrojového souboru, ve kterém je definována. Funkce ve stejném zdrojovém souboru můžou zavolat **statickou** funkci, ale funkce v jiných zdrojových souborech k nim nemůžou přistupovat přímo podle názvu. Můžete deklarovat jinou **statickou** funkci se stejným názvem v jiném zdrojovém souboru bez konfliktu.

- Funkce deklarované jako `extern` jsou viditelné v rámci všech zdrojových souborů v programu (Pokud později tuto funkci znovu nedeklarujete jako **statickou**). Jakákoli funkce může volat funkci deklarovanou jako `extern`.

- Deklarace funkce, které vynechávají specifikátor třídy úložiště, jsou ve výchozím nastavení deklarovány jako `extern`.

**Specifické pro Microsoft**

Společnost Microsoft umožňuje předefinování `extern` identifikátoru jako **statického**.

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také

[Třídy úložiště jazyka C](../c-language/c-storage-classes.md)
