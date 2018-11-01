---
title: 'Postupy: Vytváření a používání instancí objektů CComPtr a CComQIPtr'
ms.custom: how-to
ms.date: 11/04/2016
ms.topic: conceptual
ms.assetid: b0356cfb-12cc-4ee8-b988-8311ed1ab5e0
ms.openlocfilehash: 8065e0b8782c1c28d83aa6fc9690150793fe51ee
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/31/2018
ms.locfileid: "50518700"
---
# <a name="how-to-create-and-use-ccomptr-and-ccomqiptr-instances"></a>Postupy: Vytváření a používání instancí objektů CComPtr a CComQIPtr

V klasickém programování Windows jsou knihovny často implementovány jako objekty modelu COM (nebo přesněji řečeno, jako serverů modelu COM). Mnoho součásti operačního systému Windows jsou implementovány jako serverů modelu COM a knihovny v tomto formuláři zadejte velkého počtu přispěvatelů. Informace o základy modelu COM naleznete v tématu [modelu COM (Component Object)](/windows/desktop/com/component-object-model--com--portal).

Při vytváření instance objektu modelu COM (Component Object), ukládání ukazatel rozhraní inteligentním ukazatelem modelu COM, který provádí pomocí volání pro počítání odkazů `AddRef` a `Release` v destruktoru. Pokud používáte aktivní šablony knihovny (ATL) nebo třídy knihovny MFC (Microsoft Foundation), použijte `CComPtr` inteligentního ukazatele. Pokud nepoužíváte knihovny ATL nebo MFC, použijte `_com_ptr_t`. Protože neexistuje žádný COM ekvivalentní `std::unique_ptr`, použijte tyto inteligentní ukazatele pro jednoho vlastníka a vlastník více scénářů. Obě `CComPtr` a `ComQIPtr` podporu přesunout operací, které mají odkazy na r-hodnoty.

## <a name="example"></a>Příklad

Následující příklad ukazuje, jak používat `CComPtr` k vytvoření instance objektu COM a získání ukazatele na jeho rozhraní. Všimněte si, že `CComPtr::CoCreateInstance` členská funkce se používá k vytvoření objektu modelu COM, nikoli funkci Win32, který má stejný název.

[!code-cpp[COM_smart_pointers#01](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_1.cpp)]

`CComPtr` a jeho příbuzných jsou součástí knihovny ATL a jsou definovány v \<atlcomcli.h >. `_com_ptr_t` je deklarován v \<comip.h >. Kompilátor vytvoří specializace `_com_ptr_t` při generuje obálkové třídy knihovny typů.

## <a name="example"></a>Příklad

Knihovna ATL poskytuje také `CComQIPtr`, který má jednodušší syntaxí pro dotazování se objektu modelu COM pro načtení další rozhraní. Doporučujeme však `CComPtr` protože udělá všechno, co to `CComQIPtr` můžete provést a sémanticky více konzistentní s nezpracované ukazatele rozhraní modelu COM. Pokud používáte `CComPtr` se dotázat na rozhraní, se umístí nový ukazatel rozhraní do výstupní parametr. Pokud volání selže, je vrácena HRESULT, což je typické model COM. S `CComQIPtr`, vrácená hodnota je ukazatel sám a pokud selže volání interní návratovou hodnotu HRESULT je nepřístupný. Následující dva řádky zobrazit jak zpracování mechanismech chyb `CComPtr` a `CComQIPtr` lišit.

[!code-cpp[COM_smart_pointers#02](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_2.cpp)]

## <a name="example"></a>Příklad

`CComPtr` specializace zajišťující IDispatch, které umožňuje ukládat odkazy na komponenty modelu COM pro automatizaci a vyvolávat metody v rozhraní pomocí pozdní vazbu. `CComDispatchDriver` Definice TypeDef pro `CComQIPtr<IDispatch, &IIDIDispatch>`, což je implicitně převést na `CComPtr<IDispatch>`. Jakmile tyto tři názvy se zobrazí v kódu, je tedy ekvivalentní `CComPtr<IDispatch>`. Následující příklad ukazuje, jak získat ukazatel na objektový model aplikace Microsoft Word s použitím `CComPtr<IDispatch>`.

[!code-cpp[COM_smart_pointers#03](../cpp/codesnippet/CPP/how-to-create-and-use-ccomptr-and-ccomqiptr-instances_3.cpp)]

## <a name="see-also"></a>Viz také:

[Inteligentní ukazatele](../cpp/smart-pointers-modern-cpp.md)