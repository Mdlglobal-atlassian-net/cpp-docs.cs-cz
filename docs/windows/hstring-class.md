---
title: Hstring – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- corewrappers/Microsoft::WRL::Wrappers::HString
dev_langs:
- C++
ms.assetid: 6709dd2e-8d72-4675-8ec7-1baa7d71854d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 868d0a4e2d84add447c95bfcd9690c8a17850718
ms.sourcegitcommit: d5d6bb9945c3550b8e8864b22b3a565de3691fde
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/06/2018
ms.locfileid: "39571448"
---
# <a name="hstring-class"></a>HString – třída
Pomocná třída pro Správa životního cyklu HSTRING pomocí vzoru RAII.
  
## <a name="syntax"></a>Syntaxe  
  
```cpp  
class HString;  
```  
  
## <a name="remarks"></a>Poznámky  
 Modul Windows Runtime poskytuje přístup k řetězcům prostřednictvím popisovače HSTRING. **HString** třída poskytuje praktické funkce a operátory pro zjednodušení práce s popisovači HSTRING. Tato třída dokáže zpracovat životnost HSTRING vlastní prostřednictvím vzoru RAII. 
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[HString::HString – konstruktor](../windows/hstring-hstring-constructor.md)|Inicializuje novou instanci třídy **HString** třídy.|  
|[HString::~HString – destruktor](../windows/hstring-tilde-hstring-destructor.md)|Odstraní aktuální instanci aplikace **HString** třídy.|  
  
### <a name="members"></a>Členové  
  
|Název|Popis|  
|----------|-----------------|  
|[HString::Set – metoda](../windows/hstring-set-method.md)|Nastaví hodnotu aktuální **HString** objektu zadaného řetězce širokého znaku nebo **HString** parametru.|  
|[HString::Attach – metoda](../windows/hstring-attach-method.md)|Přidruží zadaný **HString** objektu s aktuálním **HString** objektu.|  
|[HString::CopyTo – metoda](../windows/hstring-copyto-method.md)|Zkopíruje aktuální **HString** objektu na objekt HSTRING.|  
|[HString::Detach – metoda](../windows/hstring-detach-method.md)|Zruší přidružení zadaného **HString** objekt ze základní hodnoty.|  
|[HString::GetAddressOf – metoda](../windows/hstring-getaddressof-method.md)|Načte ukazatel na podkladové popisovač HSTRING.|  
|[HString::Get – metoda](../windows/hstring-get-method.md)|Načte hodnotu podkladového popisovače HSTRING.|  
|[HString::Release – metoda](../windows/hstring-release-method.md)|Odstraní hodnotu řetězce a inicializuje aktuální **HString** objektu na prázdnou hodnotu.|  
|[HString::MakeReference – metoda](../windows/hstring-makereference-method.md)|Vytvoří `HStringReference` objekt ze zadaného parametru řetězce.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[HString::Operator= – operátor](../windows/hstring-operator-assign-operator.md)|Přesune hodnotu jiného **HString** objektů na aktuální **HString** objektu.|  
|[HString::Operator== – operátor](../windows/hstring-operator-equality-operator.md)|Určuje, zda se tyto dva parametry rovnají.|  
|[HString::Operator!= – operátor](../windows/hstring-operator-inequality-operator.md)|Určuje, zda dva parametry nerovnají.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `HString`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** corewrappers.h  
  
 **Namespace:** Microsoft::WRL:: wrappers –  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL::Wrappers – obor názvů](../windows/microsoft-wrl-wrappers-namespace.md)