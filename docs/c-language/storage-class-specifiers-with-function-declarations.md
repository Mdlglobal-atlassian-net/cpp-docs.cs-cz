---
title: Specifikátory třídy úložiště s deklaracemi funkce | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 8816ac8917281ed19dfc1afe9e12d302a3423f74
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/18/2018
ms.locfileid: "46111404"
---
# <a name="storage-class-specifiers-with-function-declarations"></a>Specifikátory třídy úložiště s deklaracemi funkce

Můžete použít buď **statické** nebo `extern` specifikátor třídy úložiště v deklaracích funkcí. Funkce mají vždy globální životnost.

**Specifické pro Microsoft**

Deklarace funkce na vnitřní úrovni mají stejný význam jako deklarace funkce na vnější úrovni. To znamená, že funkce je viditelná z místa deklarace ve zbytku jednotky překladu i v případě, že je deklarována v místním oboru.

**Specifické pro END Microsoft**

Pravidla viditelnosti pro funkce se mírně liší od pravidel pro proměnné, a to takto:

- Funkce deklarovaná jako **statické** je viditelná pouze v rámci zdrojového souboru, ve kterém je definována. Funkce ve stejném zdrojovém souboru mohou volat **statické** , ale funkce v jiných zdrojových souborech nelze přistupovat přímo podle názvu. Lze deklarovat jinou **statické** funkce se stejným názvem v odlišném zdrojovém souboru bez konfliktu.

- Funkce deklarované jako `extern` jsou viditelné ve všech zdrojových souborech programu (Pokud je později nepředeklarujete jako **statické**). Jakákoli funkce může volat funkci deklarovanou jako `extern`.

- Deklarace funkce, které vynechávají specifikátor třídy úložiště, jsou ve výchozím nastavení deklarovány jako `extern`.

**Specifické pro Microsoft**

Společnost Microsoft umožňuje předefinování `extern` identifikátor jako **statické**.

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také

[Třídy úložiště jazyka C](../c-language/c-storage-classes.md)