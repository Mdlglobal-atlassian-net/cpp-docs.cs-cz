---
title: "HString – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs: C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 3e8d66f134eef5f2ecb75b30fd68874418dbc49d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="hstring-class"></a>HString – třída
Pomocná třída pro správu životnost HSTRING pomocí RAII vzoru.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>Poznámky  
 Prostředí Windows Runtime poskytuje přístup k řetězce prostřednictvím HSTRING obslužné rutiny. HString – třída poskytuje funkce pro usnadnění práce a operátory pro zjednodušení práce HSTRING obslužné rutiny. Tato třída může zpracovávat životnost HSTRING vlastní prostřednictvím RAII vzor. 
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[HString::HString – konstruktor](../windows/hstring-hstring-constructor.md)|Inicializuje novou instanci třídy HString.|  
|[HString::~HString – destruktor](../windows/hstring-tilde-hstring-destructor.md)|Zničí aktuální instance třídy HString.|  
  
### <a name="members"></a>Členové  
  
|Název|Popis|  
|----------|-----------------|  
|[HString::Set – metoda](../windows/hstring-set-method.md)|Nastaví hodnotu aktuální objekt HString zadaný řetězec široká charakterová nebo HString parametr.|  
|[HString::Attach – metoda](../windows/hstring-attach-method.md)|Zadaný objekt HString přidruží aktuální objekt HString.|  
|[HString::CopyTo – metoda](../windows/hstring-copyto-method.md)|Kopie aktuální HString objektu na objekt HSTRING.|  
|[HString::Detach – metoda](../windows/hstring-detach-method.md)|Zadaný objekt HString od základní hodnoty zrušíte.|  
|[HString::GetAddressOf – metoda](../windows/hstring-getaddressof-method.md)|Načte ukazatel na základní HSTRING popisovač.|  
|[HString::Get – metoda](../windows/hstring-get-method.md)|Načte hodnotu základní HSTRING popisovač.|  
|[HString::Release – metoda](../windows/hstring-release-method.md)|Odstraní základní hodnotu řetězce a intializes aktuální objekt HString na prázdnou hodnotu.|  
|[HString::MakeReference – metoda](../windows/hstring-makereference-method.md)|Vytvoří objekt HStringReference z parametr zadaný řetězec.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[HString::Operator= – operátor](../windows/hstring-operator-assign-operator.md)|Hodnota jiného objektu HString přesune na aktuální objekt HString.|  
|[HString::Operator== – operátor](../windows/hstring-operator-equality-operator.md)|Určuje, zda dva parametry jsou stejné.|  
|[HString::Operator!= – operátor](../windows/hstring-operator-inequality-operator.md)|Určuje, zda dva parametry nejsou stejné.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HString`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)