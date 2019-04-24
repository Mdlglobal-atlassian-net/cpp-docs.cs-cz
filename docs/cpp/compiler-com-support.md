---
title: Podpora kompilátoru modelu COM
ms.date: 11/04/2016
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: f0b1d6280dc27641287de8fe539cd3a148048245
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62154835"
---
# <a name="compiler-com-support"></a>Podpora kompilátoru modelu COM

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Kompilátor Visual C++ může přímo číst knihovny typů object model (COM) komponenty a přeloží obsah do zdrojového kódu jazyka C++, které mohou být součástí kompilace. Jazyková rozšíření jsou k dispozici pro usnadnění COM programování na straně klienta.

S použitím [#import – direktiva preprocesoru](../preprocessor/hash-import-directive-cpp.md), kompilátor může číst knihovnu typů a převést ji do soubor hlaviček jazyka C++, který popisuje COM rozhraní jako třídy. Sada `#import` atributy je k dispozici pro uživatelský ovládací prvek obsahu pro výsledný souborů hlaviček knihoven typů.

Můžete použít [__declspec](../cpp/declspec.md) rozšířeného atributu [uuid](../cpp/uuid-cpp.md) přiřadit objekt modelu COM globálně jedinečný identifikátor (GUID). Klíčové slovo [__uuidof](../cpp/uuidof-operator.md) je možné extrahovat identifikátor GUID přidružený objekt modelu COM. Jiné **__declspec** atribut [vlastnost](../cpp/property-cpp.md), lze použít k určení `get` a `set` metody pro datový člen objektu modelu COM.

Sada třídy a globální funkce modelu COM podpora se poskytuje pro podporu `VARIANT` a `BSTR` typy, implementovat inteligentní ukazatele a zapouzdření objektu chyby vyvolané `_com_raise_error`:

- [Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Specifické pro END Microsoft**

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)<br/>
[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)