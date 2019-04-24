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

Můžete použít buď **statické** nebo `extern` specifikátor třídy úložiště v deklaracích funkcí. Funkce mají vždy globální životnost.

**Microsoft Specific**

Deklarace funkce na vnitřní úrovni mají stejný význam jako deklarace funkce na vnější úrovni. To znamená, že funkce je viditelná z místa deklarace ve zbytku jednotky překladu i v případě, že je deklarována v místním oboru.

**Specifické pro END Microsoft**

Pravidla viditelnosti pro funkce se mírně liší od pravidel pro proměnné, a to takto:

- Funkce deklarovaná jako **statické** je viditelná pouze v rámci zdrojového souboru, ve kterém je definována. Funkce ve stejném zdrojovém souboru mohou volat **statické** , ale funkce v jiných zdrojových souborech nelze přistupovat přímo podle názvu. Lze deklarovat jinou **statické** funkce se stejným názvem v odlišném zdrojovém souboru bez konfliktu.

- Funkce deklarované jako `extern` jsou viditelné ve všech zdrojových souborech programu (Pokud je později nepředeklarujete jako **statické**). Jakákoli funkce může volat funkci deklarovanou jako `extern`.

- Deklarace funkce, které vynechávají specifikátor třídy úložiště, jsou ve výchozím nastavení deklarovány jako `extern`.

**Microsoft Specific**

Společnost Microsoft umožňuje předefinování `extern` identifikátor jako **statické**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Třídy úložiště jazyka C](../c-language/c-storage-classes.md)
