---
title: "Ftmbase::marshalinterface – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::MarshalInterface
dev_langs: C++
helpviewer_keywords: MarshalInterface method
ms.assetid: fc8421b4-06e4-4925-b908-c285fe4790d2
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 2b6bd889a20c2c31de8e5fb6d11990fc2579ef2d
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ftmbasemarshalinterface-method"></a>FtmBase::MarshalInterface – metoda
Zapíše do datového proudu data potřebná pro inicializaci objektu proxy v některé procesu klienta.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP MarshalInterface(  
   __in IStream *pStm,  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `pStm`  
 Ukazatel do datového proudu má být použit při zařazování.  
  
 `riid`  
 Odkaz na identifikátor rozhraní být zařazena. Toto rozhraní musí být odvozen z rozhraní IUnknown.  
  
 `pv`  
 Ukazatel na ukazatel rozhraní zařazována; může mít hodnotu NULL, pokud má volající nemá požadované rozhraní ukazatel.  
  
 `dwDestContext`  
 Cílový kontext, kde má být zařazeny specifikované rozhraní.  
  
 Zadejte jeden nebo více hodnot výčtu MSHCTX.  
  
 Unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu na stejném počítači jako aktuální proces (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Vyhrazeno pro budoucí použití; musí být nula.  
  
 `mshlflags`  
 Určuje, jestli má být přenesen zpět do procesu klienta je data, která mají být zařazené – obvyklý případ – nebo zapisovat do globální tabulky, kde se dá načíst více klientů.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK  
 Ukazatel rozhraní byl úspěšně zařazené.  
  
 E_NOINTERFACE  
 Zadané rozhraní není podporováno.  
  
 STG_E_MEDIUMFULL  
 Datový proud je plná.  
  
 E_FAIL  
 Operace se nezdařila.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)