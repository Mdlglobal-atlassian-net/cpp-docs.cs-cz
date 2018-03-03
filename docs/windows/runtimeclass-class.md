---
title: "RuntimeClass – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- implements/Microsoft::WRL::RuntimeClass
dev_langs:
- C++
helpviewer_keywords:
- RuntimeClass class
ms.assetid: d52f9d1a-98e5-41f2-a143-8fb629dd0727
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: d5c75492b55cd1c238798d3500e2157738c3c58f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/21/2017
---
# <a name="runtimeclass-class"></a>RuntimeClass – třída
Představuje třídu WinRT nebo COM, která dědí zadaný rozhraní a poskytuje zadané prostředí Windows Runtime, classic COM a slabé odkaz na podporu.  
  
Tato třída poskytuje standardní implementace třídy WinRT a modelu COM, poskytuje implementace `QueryInterface`, `AddRef`, `Release` atd., spravuje počet odkazů modulu a podporu pro zajištění objekt factory třídy pro activatable objekty.
  
## <a name="syntax"></a>Syntaxe  
  
```
template <typename ...TInterfaces> class RuntimeClass
template <unsigned int classFlags, typename ...TInterfaces> class RuntimeClass;
```
  
#### <a name="parameters"></a>Parametry  
 `classFlags`  
Volitelný parametr. Kombinace jednoho nebo více [RuntimeClassType](../windows/runtimeclasstype-enumeration.md) hodnot výčtu. `__WRL_CONFIGURATION_LEGACY__` Makro lze definovat za účelem změnit výchozí hodnotu classFlags pro všechny třídy za běhu v projektu. Pokud definované, RuntimeClass instance jsou jiný agilní ve výchozím nastavení. Pokud není definované, RuntimeClass instance jsou agilní ve výchozím nastavení. Aby se zabránilo nejednoznačnosti vždycky zadat Microsoft::WRL::FtmBase v `TInterfaces` nebo RuntimeClassType::InhibitFtmBase. Poznámka: Pokud jsou obě používá objekt InhibitFtmBase a FtmBase bude agile.
 
 `TInterfaces`  
Seznam rozhraní objekt implementuje nad rámec IUnknown, IInspectable nebo dalších rozhraní řízené [RuntimeClassType](../windows/runtimeclasstype-enumeration.md). Je taky mohou ostatní třídy pocházet ze, zejména Microsoft::WRL::FtmBase byl objekt agilní a způsobit, že ho implementovat imarshal – seznam.
  
## <a name="members"></a>Členové  
`RuntimeClassInitialize`Funkci, která inicializuje objekt, pokud funkce šablony makeandinitialize – slouží k vytvoření objektu. Pokud se inicializace vrátí S_OK, pokud daný objekt byl úspěšně inicializován nebo COM kód chyby. Kód chyby COM jako návratová hodnota makeandinitialize – rozšířena. Všimněte si, že RuntimeClassInitialize metoda není volána, pokud funkce šablony zkontrolujte slouží k vytvoření objektu.

### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[RuntimeClass::RuntimeClass – konstruktor](../windows/runtimeclass-runtimeclass-constructor.md)|Inicializuje aktuální instanci RuntimeClass – třída.|  
|[RuntimeClass::~RuntimeClass – destruktor](../windows/runtimeclass-tilde-runtimeclass-destructor.md)|Deinitializes aktuální instance třídy RuntimeClass.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
Toto je podrobností implementace.
  
## <a name="requirements"></a>Požadavky  
**Záhlaví:** implements.h  
  
**Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
[Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)
