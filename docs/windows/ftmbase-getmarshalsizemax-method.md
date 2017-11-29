---
title: "Ftmbase::getmarshalsizemax – metoda | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: ftm/Microsoft::WRL::FtmBase::GetMarshalSizeMax
dev_langs: C++
helpviewer_keywords: GetMarshalSizeMax method
ms.assetid: b416b1bf-c73e-45d5-abb8-04921c1a0c94
caps.latest.revision: "3"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 3597d19e1bcdc6b1b14e150c66236585f8c35fb8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="ftmbasegetmarshalsizemax-method"></a>FtmBase::GetMarshalSizeMax – metoda
Získáte horní mez počtu bajtů, které jsou potřebné pro zařazování specifikované rozhraní ukazatele na zadaný objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
STDMETHODIMP GetMarshalSizeMax(  
   __in REFIID riid,  
   __in_opt void *pv,  
   __in DWORD dwDestContext,  
   __reserved void *pvDestContext,  
   __in DWORD mshlflags,  
   __out DWORD *pSize  
) override;  
```  
  
#### <a name="parameters"></a>Parametry  
 `riid`  
 Odkaz na identifikátor rozhraní být zařazena.  
  
 `pv`  
 Ukazatel rozhraní zařazována; může mít hodnotu NULL.  
  
 `dwDestContext`  
 Cílový kontext, kde má být zařazeny specifikované rozhraní.  
  
 Zadejte jeden nebo více hodnot výčtu MSHCTX.  
  
 V současné době unmarshaling situace může nastat v jiném objektu apartment aktuálního procesu (MSHCTX_INPROC) nebo v jiném procesu na stejném počítači jako aktuální proces (MSHCTX_LOCAL).  
  
 `pvDestContext`  
 Vyhrazeno pro budoucí použití; musí mít hodnotu NULL.  
  
 `mshlflags`  
 Příznak, který udává, zda data, která mají být zařazené se předává zpátky do procesu klientů – obvyklý případ – nebo zapisovat do globální tabulky, kde se dá načíst více klientů. Zadejte jeden nebo více hodnot výčtu MSHLFLAGS.  
  
 `pSize`  
 Když tato operace dokončí, ukazatel na horní mez na množství dat, která má být zapsán do zařazování datového proudu.  
  
## <a name="return-value"></a>Návratová hodnota  
 S_OK v případě úspěšného; jinak hodnota E_FAIL nebo E_NOINTERFACE.  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** ftm.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [FtmBase – třída](../windows/ftmbase-class.md)