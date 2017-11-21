---
title: "FtmBase – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase
dev_langs: C++
helpviewer_keywords: FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: a5d9fb768c4c1030a43094565aae5f88fdabf4eb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ftmbase-class"></a>FtmBase – třída
Představuje objekt volné zařazování vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags< WinRtClassicComMix >,   
   Microsoft::WRL::CloakedIid< IMarshal > >;  
```  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu "Imarshal –" v "COM – rozhraní" dílčí téma tématu "COM odkaz" v knihovně MSDN.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Ftmbase::ftmbase – konstruktor](../windows/ftmbase-ftmbase-constructor.md)|Inicializuje novou instanci třídy FtmBase.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Ftmbase::createglobalinterfacetable – metoda](../windows/ftmbase-createglobalinterfacetable-method.md)|Vytvoří tabulku globální rozhraní (GIT).|  
|[Ftmbase::disconnectobject – metoda](../windows/ftmbase-disconnectobject-method.md)|Vynuceně uvolní všechny externí připojení k objektu. Server objektu volání objektu implementace této metody před vypíná.|  
|[Ftmbase::getmarshalsizemax – metoda](../windows/ftmbase-getmarshalsizemax-method.md)|Získáte horní mez počtu bajtů, které jsou potřebné pro zařazování specifikované rozhraní ukazatele na zadaný objekt.|  
|[Ftmbase::getunmarshalclass – metoda](../windows/ftmbase-getunmarshalclass-method.md)|Získá CLSID, který COM používá k nalezení DLL obsahující kód pro odpovídající proxy server. COM načte tuto knihovnu DLL k vytvoření instance Neinicializovaný proxy serveru.|  
|[Ftmbase::marshalinterface – metoda](../windows/ftmbase-marshalinterface-method.md)|Zapíše do datového proudu data potřebná pro inicializaci objektu proxy v některé procesu klienta.|  
|[Ftmbase::releasemarshaldata – metoda](../windows/ftmbase-releasemarshaldata-method.md)|Zničí zařazené datový paket.|  
|[Ftmbase::unmarshalinterface – metoda](../windows/ftmbase-unmarshalinterface-method.md)|Inicializuje nově vytvořený proxy a vrátí ukazatele rozhraní zda proxy serveru.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[Ftmbase::marshaller_ – datový člen](../windows/ftmbase-marshaller-data-member.md)|Obsahuje odkaz na volné zařazování vláken.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `FtmBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)