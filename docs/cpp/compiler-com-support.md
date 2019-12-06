---
title: Podpora kompilátoru modelu COM
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 6ab697e5a090158b034a385e60978cff4a73f488
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857577"
---
# <a name="compiler-com-support"></a>Podpora kompilátoru modelu COM

**Specifické pro společnost Microsoft**

Kompilátor společnosti C++ Microsoft může přímo číst knihovny typů modelu COM (Component Object Model) a překládat obsah C++ do zdrojového kódu, který lze zahrnout do kompilace. Jazykové rozšíření jsou k dispozici pro usnadnění programování COM na straně klienta pro desktopové aplikace.

Pomocí [direktivy preprocesoru #import](../preprocessor/hash-import-directive-cpp.md)může kompilátor načíst knihovnu typů a převést ji do C++ hlavičkového souboru, který popisuje rozhraní COM jako třídy. Sada atributů `#import` je k dispozici pro uživatelský ovládací prvek obsahu pro výsledné soubory hlaviček knihovny typů.

Pomocí [identifikátoru UUID](../cpp/uuid-cpp.md) rozšířeného atributu [__declspec](../cpp/declspec.md) můžete přiřadit globálně jedinečný identifikátor (GUID) objektu com. Klíčové slovo [__uuidof](../cpp/uuidof-operator.md) lze použít k EXTRAKCi identifikátoru GUID přidruženého k objektu com. Další **__declspec** atribut, [vlastnost](../cpp/property-cpp.md), lze použít k určení `get` a `set` metody pro datový člen objektu com.

Sada COM podporuje globální funkce a třídy je poskytována pro podporu `VARIANT` a `BSTR` typů, implementace inteligentních ukazatelů a zapouzdření objektu Error vyvolaného `_com_raise_error`:

- [Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)<br/>
[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)
