---
title: Podpora kompilátoru modelu COM
ms.date: 05/06/2019
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
ms.openlocfilehash: 421930088dcbf9762d50b5af37d994b9008890eb
ms.sourcegitcommit: 720b74dddb1cdf4e570d55103158304ee1df81f8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/29/2019
ms.locfileid: "68606374"
---
# <a name="compiler-com-support"></a>Podpora kompilátoru modelu COM

## <a name="microsoft-specific"></a>Specifické pro Microsoft

Kompilátor společnosti C++ Microsoft může přímo číst knihovny typů modelu COM (Component Object Model) a překládat obsah C++ do zdrojového kódu, který lze zahrnout do kompilace. Jazykové rozšíření jsou k dispozici pro usnadnění programování COM na straně klienta pro desktopové aplikace.

Pomocí direktivy [preprocesoru #import](../preprocessor/hash-import-directive-cpp.md)může kompilátor načíst knihovnu typů a převést ji do C++ hlavičkového souboru, který popisuje rozhraní COM jako třídy. Sada `#import` atributů je k dispozici pro uživatelský ovládací prvek obsahu pro výsledné hlavičkové soubory knihovny typů.

Identifikátor [UUID](../cpp/uuid-cpp.md) rozšířeného atributu [__declspec](../cpp/declspec.md) můžete použít k přiřazení globálně jedinečného identifikátoru (GUID) objektu com. Klíčové slovo [__uuidof](../cpp/uuidof-operator.md) lze použít k EXTRAKCi identifikátoru GUID přidruženého k objektu com. Další atribut **__declspec** , [vlastnost](../cpp/property-cpp.md), lze použít `get` k určení metod a `set` pro datový člen objektu com.

Sada com podporuje globální funkce a třídy je poskytována pro podporu `VARIANT` typů a `BSTR` , implementaci inteligentních ukazatelů a zapouzdření objektu Error vyvolaného `_com_raise_error`:

- [Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)

- [_bstr_t](../cpp/bstr-t-class.md)

- [_com_error](../cpp/com-error-class.md)

- [_com_ptr_t](../cpp/com-ptr-t-class.md)

- [_variant_t](../cpp/variant-t-class.md)

**Specifické pro konec Microsoftu**

## <a name="see-also"></a>Viz také:

[Třídy podpory kompilátoru COM](../cpp/compiler-com-support-classes.md)<br/>
[Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)
