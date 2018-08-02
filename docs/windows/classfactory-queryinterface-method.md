---
title: ClassFactory::QueryInterface – metoda | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- module/Microsoft::WRL::ClassFactory::QueryInterface
dev_langs:
- C++
helpviewer_keywords:
- QueryInterface method
ms.assetid: 9593881f-4585-4d70-8ca6-b328918d4d6b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0c0132ddeb7a8bfa30f95d3e4c85ec03962361f3
ms.sourcegitcommit: 51f804005b8d921468775a0316de52ad39b77c3e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/02/2018
ms.locfileid: "39467089"
---
# <a name="classfactoryqueryinterface-method"></a>ClassFactory::QueryInterface – metoda
Načte ukazatel na rozhraní určené typem parametru.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHOD(  
   QueryInterface  
)(REFIID riid, _Deref_out_ void **ppvObject);  
```  
  
#### <a name="parameters"></a>Parametry  
 *riid*  
 Identifikátor rozhraní.  
  
 *ppvObject*  
 Když tato operace dokončí, ukazatel na rozhraní určené typem parametru *riid*.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěchu; v opačném případě HRESULT s popisem chyby.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** module.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [ClassFactory – třída](../windows/classfactory-class.md)