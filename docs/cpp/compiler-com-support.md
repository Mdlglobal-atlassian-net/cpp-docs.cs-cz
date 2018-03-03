---
title: "Podpora kompilátoru modelu COM | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, COM support
- COM, compiler support
ms.assetid: 76a78442-f2a4-4985-9967-67e20773f847
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: b05fdff690f8693e926011c3bc7d1738ee9be66c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-com-support"></a>Podpora kompilátoru modelu COM
## <a name="microsoft-specific"></a>Specifické pro Microsoft  
 Visual C++ compiler může přímo číst knihovny typů model (COM) objekt součásti a převede obsah do zdrojového kódu C++, které můžou být součástí kompilace. Jazyková rozšíření jsou k dispozici pro usnadnění COM programování na straně klienta.  
  
 Pomocí [#import – direktiva preprocesoru](../preprocessor/hash-import-directive-cpp.md), kompilátor může číst knihovny typů a převést jej do souboru záhlaví C++, který popisuje knihovny COM rozhraní jako třídy. Sadu `#import` atributy je k dispozici pro uživatelský ovládací prvek obsahu pro výsledný soubory hlaviček knihovny typu.  
  
 Můžete použít [__declspec](../cpp/declspec.md) rozšířených atributů [uuid](../cpp/uuid-cpp.md) přiřadit objektu COM globálně jedinečný identifikátor (GUID). Klíčové slovo [__uuidof –](../cpp/uuidof-operator.md) slouží k extrakci identifikátor GUID přidružený k objektu COM. Jiné `__declspec` atribut [vlastnost](../cpp/property-cpp.md), lze použít k určení **získat** a **nastavit** metody pro člena data objektu COM.  
  
 Poskytuje sadu COM podporu globální funkce a třídy pro podporu **VARIANT** a `BSTR` typy, implementovat chytré ukazatele a zapouzdřují objekt chyba vyvolané `_com_raise_error`:  
  
-   [Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)  
  
-   [_bstr_t](../cpp/bstr-t-class.md)  
  
-   [_com_error](../cpp/com-error-class.md)  
  
-   [_com_ptr_t –](../cpp/com-ptr-t-class.md)  
  
-   [_variant_t](../cpp/variant-t-class.md)  
  
**Konkrétní Microsoft END**  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory modelu comp kompilátoru](../cpp/compiler-com-support-classes.md)   
 [Globální funkce kompilátoru COM](../cpp/compiler-com-global-functions.md)