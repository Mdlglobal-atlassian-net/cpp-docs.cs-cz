---
title: Weakref – třída | Dokumentace Microsoftu
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- client/Microsoft::WRL::WeakRef
dev_langs:
- C++
helpviewer_keywords:
- WeakRef class
ms.assetid: 572be703-c641-496c-8af5-ad6164670ba1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 88252e6bf4a5b7cad1ee6fcd0580d29f1bf5981a
ms.sourcegitcommit: 37a10996022d738135999cbe71858379386bab3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "39641823"
---
# <a name="weakref-class"></a>WeakRef – třída
Představuje *nestálý odkaz* , který lze používat pouze modulu Windows Runtime, ne klasického modelu COM. Slabý odkaz představuje objekt, který může nebo nemusí být dostupný.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
class WeakRef : public ComPtr<IWeakReference>  
```  
  
## <a name="remarks"></a>Poznámky  
 A **WeakRef** udržuje objekt *silného odkazu*, který je přidružený k objektu a může být platný nebo neplatný. Volání `As()` nebo `AsIID()` metodu k získání silného odkazu. Silný odkaz je platný, má přístup k přidruženého objektu. Když je neplatný silný odkaz (**nullptr**), přidruženého objektu není dostupný.  
  
 A **WeakRef** objekt se obvykle používá k reprezentaci objektu, jehož existence je řízena vnějším vláknem nebo aplikací. Například sestavit **WeakRef** objekt z odkazu na objekt souboru. Když je soubor otevřen, silný odkaz je platný. Ale pokud se soubor zavře, silný odkaz níže uvedených situací.  
  
 Všimněte si, že dojde ke změně chování v [jako](../windows/weakref-as-method.md), [asiid –](../windows/weakref-asiid-method.md) a [CopyTo](../windows/weakref-copyto-method.md) metody ve Windows 10 SDK. Dříve, po volání některé z těchto metod, můžete zkontrolovat WeakRef pro **nullptr** k určení, pokud silného odkazu byl úspěšně získán, stejně jako v následujícím kódu:  
  
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
  
 Ve výše uvedeném kódu nefunguje při použití Windows 10 SDK (nebo novější). Místo toho zkontrolujte ukazatel, který byl předán pro **nullptr**.  
  
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
|[WeakRef::WeakRef – konstruktor](../windows/weakref-weakref-constructor.md)|Inicializuje novou instanci třídy **WeakRef** třídy.|  
|[WeakRef::~WeakRef – destruktor](../windows/weakref-tilde-weakref-destructor.md)|Zruší inicializaci aktuální instance **WeakRef** třídy.|  
  
### <a name="public-methods"></a>Veřejné metody  
  
|Název|Popis|  
|----------|-----------------|  
|[WeakRef::As – metoda](../windows/weakref-as-method.md)|Nastaví zadaný `ComPtr` parametr ukazatele k reprezentaci zadané rozhraní.|  
|[WeakRef::AsIID – metoda](../windows/weakref-asiid-method.md)|Nastaví zadaný `ComPtr` parametr ukazatele představující ID zadané rozhraní.|  
|[WeakRef::CopyTo – metoda](../windows/weakref-copyto-method.md)|Přiřadí ukazatel rozhraní, pokud je k dispozici k proměnné zadané ukazatele.|  
  
### <a name="public-operators"></a>Veřejné operátory  
  
|Název|Popis|  
|----------|-----------------|  
|[WeakRef::operator& – operátor](../windows/weakref-operator-ampersand-operator.md)|Vrátí `ComPtrRef` objekt, který představuje aktuální **WeakRef** objektu.|  
  
## <a name="inheritance-hierarchy"></a>Hierarchie dědičnosti  
 `ComPtr`  
  
 `WeakRef`  
  
## <a name="requirements"></a>Požadavky  
 **Záhlaví:** client.h  
  
 **Namespace:** Microsoft::WRL  
  
## <a name="see-also"></a>Viz také  
 [Microsoft::WRL – obor názvů](../windows/microsoft-wrl-namespace.md)