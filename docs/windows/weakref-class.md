---
title: "WeakRef – třída | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords: client/Microsoft::WRL::WeakRef
dev_langs: C++
helpviewer_keywords: WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 148c39f1ef38b6b20de6d50cc75352a4f30a9090
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/24/2017
---
# <a name="weakref-class"></a>WeakRef – třída
Představuje *slabé odkaz* které lze použít pouze prostředí Windows Runtime, není klasického modelu COM. Slabé odkazy představuje objekt, který může nebo nemusí být dostupné.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## <a name="remarks"></a>Poznámky  
 Objekt WeakRef udržuje *silné odkaz*, která je přidružená objektu a může být platný nebo neplatný. Volejte metodu As() nebo AsIID() k získání silné odkazu. Když je silné odkaz platný, má přístup přidruženého objektu. Když je neplatný odkaz na silné (`nullptr`), přidruženého objektu je nedostupná.  
  
 WeakRef objekt se obvykle používá k reprezentování objekt, jehož existence řídí na externí vlákna nebo aplikaci. Můžete například vytvořte objekt WeakRef z odkaz na objekt souboru. Je-li otevřít soubor, je silné odkaz platný. Ale pokud soubor se zavřel, silné odkaz bude neplatná.  
  
 Všimněte si, že dojde ke změně chování v [jako](../windows/weakref-as-method.md), [asiid –](../windows/weakref-asiid-method.md) a [CopyTo](../windows/weakref-copyto-method.md) metody v sadě Windows 10 SDK. Dříve, po volání metody některé z těchto metod, můžete zkontrolovat WeakRef pro `nullptr` k určení, pokud silné odkaz byl úspěšně získanou, jako v následujícím kódu:  
  
```cpp  
WeakRef wr;  
strongComptrRef.AsWeak(&wr);  
  
// Now suppose that the object strongComPtrRef points to no longer exists  
// and the following code tries to get a strong ref from the weak ref:  
ComPtr<ISomeInterface> strongRef;  
HRESULT hr = wr.As(&strongRef);  
  
// This check won't work with the Windows 10 SDK version of the library.  
// Check the input pointer instead.  
if(wr == nullptr)  
{  
    wprintf(L"Couldn’t get strong ref!");  
}  
  
```  
  
 Výše uvedený kód nefunguje, pokud používáte Windows 10 SDK (nebo novější). Místo toho zkontrolujte ukazatele, který byl předán pro `nullptr`.  
  
```cpp  
if (strongRef == nullptr)  
{  
    wprintf(L"Couldn't get strong ref!");  
 }  
  
```  
  
## <a name="members"></a>Členové  
  
### <a name="public-constructors"></a>Veřejné konstruktory  
  
|Název|Popis|  
|----------|-----------------|  
|[Weakref::weakref – konstruktor](../windows/weakref-weakref-constructor.md)|Inicializuje novou instanci třídy WeakRef.|  
|[WeakRef:: ~ weakref – destruktor](../windows/weakref-tilde-weakref-destructor.md)|Deinitializes aktuální instance třídy WeakRef.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[Weakref::AS – metoda](../windows/weakref-as-method.md)|Nastaví zadaný parametr ukazatel ComPtr představují specifikované rozhraní.|  
|[Weakref::asiid – metoda](../windows/weakref-asiid-method.md)|Nastaví zadaný parametr ukazatel ComPtr představují ID specifikované rozhraní.|  
|[Weakref::CopyTo – metoda](../windows/weakref-copyto-method.md)|Přiřadí ukazatele rozhraní, pokud je k dispozici, proměnnou zadaný ukazatele.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[WeakRef::operator & – operátor](../windows/weakref-operator-ampersand-operator.md)|Vrátí objekt ComPtrRef, který představuje aktuální objekt WeakRef.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ComPtr`  
  
 `WeakRef`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL Namespace](../windows/microsoft-wrl-namespace.md)