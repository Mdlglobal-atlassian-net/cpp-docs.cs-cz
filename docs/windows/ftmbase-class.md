---
title: FtmBase – třída | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- ftm/Microsoft::WRL::FtmBase
dev_langs:
- C++
helpviewer_keywords:
- FtmBase class
ms.assetid: 275f3b71-2975-4f92-89e7-d351e96496df
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7bcc003811a747569f22f6b2603faf72096dd049
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="ftmbase-class"></a>FtmBase – třída
Představuje objekt volné zařazování vláken.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
  
class FtmBase : public Microsoft::WRL::Implements<  
   Microsoft::WRL::RuntimeClassFlags<WinRtClassicComMix>,   
   Microsoft::WRL::CloakedIid<IMarshal> >;  
```  
  
## <a name="remarks"></a>Poznámky  
 Další informace najdete v tématu "Imarshal –" v "COM – rozhraní" dílčí téma tématu "COM odkaz" v knihovně MSDN.  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[FtmBase::FtmBase – konstruktor](../windows/ftmbase-ftmbase-constructor.md)|Inicializuje novou instanci třídy FtmBase.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[FtmBase::CreateGlobalInterfaceTable – metoda](../windows/ftmbase-createglobalinterfacetable-method.md)|Vytvoří tabulku globální rozhraní (GIT).|  
|[FtmBase::DisconnectObject – metoda](../windows/ftmbase-disconnectobject-method.md)|Vynuceně uvolní všechny externí připojení k objektu. Server objektu volání objektu implementace této metody před vypíná.|  
|[FtmBase::GetMarshalSizeMax – metoda](../windows/ftmbase-getmarshalsizemax-method.md)|Získáte horní mez počtu bajtů, které jsou potřebné pro zařazování specifikované rozhraní ukazatele na zadaný objekt.|  
|[FtmBase::GetUnmarshalClass – metoda](../windows/ftmbase-getunmarshalclass-method.md)|Získá CLSID, který COM používá k nalezení DLL obsahující kód pro odpovídající proxy server. COM načte tuto knihovnu DLL k vytvoření instance Neinicializovaný proxy serveru.|  
|[FtmBase::MarshalInterface – metoda](../windows/ftmbase-marshalinterface-method.md)|Zapíše do datového proudu data potřebná pro inicializaci objektu proxy v některé procesu klienta.|  
|[FtmBase::ReleaseMarshalData – metoda](../windows/ftmbase-releasemarshaldata-method.md)|Zničí zařazené datový paket.|  
|[FtmBase::UnmarshalInterface – metoda](../windows/ftmbase-unmarshalinterface-method.md)|Inicializuje nově vytvořený proxy a vrátí ukazatele rozhraní zda proxy serveru.|  
  
### <a name="public-data-members"></a>Veřejné datové členy  
  
|Název|Popis|  
|----------|-----------------|  
|[FtmBase::marshaller_ – datový člen](../windows/ftmbase-marshaller-data-member.md)|Obsahuje odkaz na volné zařazování vláken.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `FtmBase`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)