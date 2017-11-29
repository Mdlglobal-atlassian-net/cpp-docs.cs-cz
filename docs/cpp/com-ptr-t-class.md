---
title: "_com_ptr_t – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords: _com_ptr_t
dev_langs: C++
helpviewer_keywords: _com_ptr_t class
ms.assetid: 3753a8a0-03d4-4cfd-8a9a-74872ea53971
caps.latest.revision: "8"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: d395b6981e167bf759e0e26577dca962632a22c3
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="comptrt-class"></a>_com_ptr_t – třída
**Konkrétní Microsoft**  
  
 A `_com_ptr_t` objekt zapouzdří ukazatele rozhraní COM a se nazývá "smart" ukazatel. Tato třída šablony spravuje přidělení prostředků a navrácení prostřednictvím volání funkce **IUnknown** členské funkce: `QueryInterface`, `AddRef`, a **verze**.  
  
 Chytré ukazatele je obvykle odkazuje v definici typedef poskytované **_COM_SMARTPTR_TYPEDEF** makro. Toto makro přebírá název rozhraní a identifikátory IID a deklaruje specializace `_com_ptr_t` s názvem rozhraní plus příponu `Ptr`. Příklad:  
  
```  
_COM_SMARTPTR_TYPEDEF(IMyInterface, __uuidof(IMyInterface));  
```  
  
 deklaruje `_com_ptr_t` specializace **IMyInterfacePtr**.  
  
 Sadu [funkce šablony](../cpp/relational-function-templates.md), nejsou členy této šablony třídy, podporu porovnání s inteligentní ukazatel na pravé straně operátoru porovnání.  
  
### <a name="construction"></a>Konstrukce  
  
|||  
|-|-|  
|[_com_ptr_t –](../cpp/com-ptr-t-com-ptr-t.md)|Vytvoří `_com_ptr_t` objektu.|  
  
### <a name="low-level-operations"></a>Operace nízké úrovně  
  
|||  
|-|-|  
|[Addref –](../cpp/com-ptr-t-addref.md)|Volání `AddRef` členské funkce **IUnknown** na ukazatel zapouzdřené rozhraní.|  
|[Připojení](../cpp/com-ptr-t-attach.md)|Zapouzdří ukazatel nezpracovaná rozhraní tento inteligentní ukazatel typu.|  
|[CreateInstance –](../cpp/com-ptr-t-createinstance.md)|Vytvoří novou instanci objektu zadané **CLSID** nebo **ProgID**.|  
|[Odpojení](../cpp/com-ptr-t-detach.md)|Extrahuje a vrátí zapouzdřený ukazatel rozhraní.|  
|[Getactiveobject –](../cpp/com-ptr-t-getactiveobject.md)|Připojí k existující instanci objekt daný **CLSID** nebo **ProgID**.|  
|[Getinterfaceptr –](../cpp/com-ptr-t-getinterfaceptr.md)|Vrátí ukazatel zapouzdřené rozhraní.|  
|[QueryInterface –](../cpp/com-ptr-t-queryinterface.md)|Volání `QueryInterface` členské funkce **IUnknown** na ukazatel zapouzdřené rozhraní.|  
|[Vydaná verze](../cpp/com-ptr-t-release.md)|Volání **verze** členské funkce **IUnknown** na ukazatel zapouzdřené rozhraní.|  
  
### <a name="operators"></a>Operátory  
  
|||  
|-|-|  
|[operátor =](../cpp/com-ptr-t-operator-equal.md)|Přiřadí novou hodnotu na stávající `_com_ptr_t` objektu.|  
|[operátory ==,! =, \<, >, \<=, > =](../cpp/com-ptr-t-relational-operators.md)|Porovnání chytré ukazatele objekt, který má jinou inteligentní ukazatel ukazatel nezpracovaná rozhraní nebo **NULL**.|  
|[Extraktory](../cpp/com-ptr-t-extractors.md)|Extrahuje zapouzdřený ukazatel rozhraní COM.|  
  
**Konkrétní Microsoft END**  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** comip.h  
  
 **Lib:** comsuppw.lib nebo comsuppwd.lib (viz [/Zc: wchar_t (wchar_t je nativní typ)](../build/reference/zc-wchar-t-wchar-t-is-native-type.md) informace)  
  
## <a name="see-also"></a>Viz také  
 [Třídy podpory modelu comp kompilátoru](../cpp/compiler-com-support-classes.md)