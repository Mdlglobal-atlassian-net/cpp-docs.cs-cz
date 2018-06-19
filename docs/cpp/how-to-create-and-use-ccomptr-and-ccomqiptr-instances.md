---
title: 'Postupy: vytváření a používání CComPtr a CComQIPtr instance | Microsoft Docs'
ms.custom: how-to
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6c63eb1657cd00580197e0571a40e9a7545688dd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/03/2018
ms.locfileid: "32415449"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Postupy: Vytváření a používání instancí objektů CComPtr a CComQIPtr
V classic programování v systému Windows, jsou knihovny často implementovány jako objekty modelu COM (nebo přesněji řečeno, jako servery COM). Mnoho součásti systému Windows jsou implementované jako servery COM a počet přispěvatelů poskytnout knihovny v tomto formuláři. Informace o základech COM najdete v tématu [modelu COM (Component Object)](http://msdn.microsoft.com/en-us/3578ca42-a4b6-44b3-ad5b-aeb5fa61f3f4).  
  
 Když je vytvoření instance objektu modelu COM (Component Object), Uložit ukazatel rozhraní v inteligentní ukazatel COM, který provádí počítání pomocí volání referencí `AddRef` a `Release` v destruktoru. Pokud používáte Active šablony Library (ATL) nebo Microsoft Foundation Class Library (MFC), použijte `CComPtr` chytré ukazatele. Pokud nepoužíváte ATL nebo MFC, použijte `_com_ptr_t`. Protože je ekvivalentní žádné COM `std::unique_ptr`, použijte tyto chytré ukazatele pro scénáře vlastníka jedním i několika vlastníka. Obě `CComPtr` a `ComQIPtr` podporu přesunout operace, které odkazují rvalue.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak používat `CComPtr` k vytvoření instance objektu COM a získání ukazatele na jeho rozhraní. Všimněte si, že `CComPtr::CoCreateInstance` – členská funkce se používá k vytvoření objektu COM, nikoli Win32 funkce, která má stejný název.  
  
 [!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]  
  
 `CComPtr` a jeho příbuzných jsou součástí knihovny ATL a jsou definovány v \<atlcomcli.h >. `_com_ptr_t` je deklarován v \<comip.h >. Kompilátor vytvoří specializací `_com_ptr_t` při vygeneruje Obálka – třídy pro knihovny typů.  
  
## <a name="example"></a>Příklad  
 Také poskytuje ATL `CComQIPtr`, který má jednodušší syntaxi pro dotazování objektu COM pro načtení další rozhraní. Doporučujeme však `CComPtr` protože provádí vše, `CComQIPtr` můžete provést a sémanticky více konzistentní se nezpracovaná ukazatele rozhraní COM. Pokud používáte `CComPtr` se dotázat na rozhraní, nové ukazatel rozhraní je umístěn v výstupní parametr. Pokud volání selže, je vrácen HRESULT, což je obvyklý COM. S `CComQIPtr`, vrácená hodnota je ukazatel sám sebe, a pokud volání selže, interní návratovou hodnotu HRESULT není přístupný. Následující dva řádků jak zobrazit chyba zpracování mechanismech `CComPtr` a `CComQIPtr` lišit.  
  
 [!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]  
  
## <a name="example"></a>Příklad  
 `CComPtr` poskytuje specializace pro IDispatch, což umožňuje ukládat ukazatele na komponenty COM automatizaci a vyvolání metody na rozhraní pomocí pozdní vazba. `CComDispatchDriver` je typedef pro `CComQIPtr<IDispatch, &IIDIDispatch>`, což je implicitně převést na `CComPtr<IDispatch>`. Proto když všechny tyto tři názvy se zobrazí v kódu, je ekvivalentní `CComPtr<IDispatch>`. Následující příklad ukazuje, jak získat pomocí ukazatele na objektový model Microsoft Word `CComPtr<IDispatch>`.  
  
 [!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]  
  
## <a name="see-also"></a>Viz také  
 [Chytré ukazatele](../cpp/smart-pointers-modern-cpp.md)