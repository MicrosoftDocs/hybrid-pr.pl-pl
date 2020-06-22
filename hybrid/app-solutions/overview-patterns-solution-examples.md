---
title: Wzorce hybrydowe i przykłady rozwiązań dla platformy Azure i centrum Azure Stack
description: Omówienie wzorców hybrydowych i przykładów rozwiązań służących do uczenia się i tworzenia rozwiązań hybrydowych na platformie Azure i Azure Stack centrum.
author: BryanLa
ms.topic: overview
ms.date: 11/05/2019
ms.author: bryanla
ms.reviewer: anajod
ms.lastreviewed: 11/05/2019
ms.openlocfilehash: ab0eb885e7b0fefaca8991522712652f979d8712
ms.sourcegitcommit: bb3e40b210f86173568a47ba18c3cc50d4a40607
ms.translationtype: MT
ms.contentlocale: pl-PL
ms.lasthandoff: 06/17/2020
ms.locfileid: "84910916"
---
# <a name="hybrid-patterns-and-solution-examples-for-azure-and-azure-stack"></a><span data-ttu-id="1ac31-103">Wzorce hybrydowe i przykłady rozwiązań dla platformy Azure i Azure Stack</span><span class="sxs-lookup"><span data-stu-id="1ac31-103">Hybrid patterns and solution examples for Azure and Azure Stack</span></span>

<span data-ttu-id="1ac31-104">Firma Microsoft udostępnia produkty i rozwiązania platformy Azure i Azure Stack jako jeden spójny ekosystem platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="1ac31-104">Microsoft provides Azure and Azure Stack products and solutions as one consistent Azure ecosystem.</span></span> <span data-ttu-id="1ac31-105">Rodzina Microsoft Azure Stack to rozszerzenie platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="1ac31-105">The Microsoft Azure Stack family is an extension of Azure.</span></span>

## <a name="the-hybrid-cloud-and-hybrid-apps"></a><span data-ttu-id="1ac31-106">Chmura hybrydowa i aplikacje hybrydowe</span><span class="sxs-lookup"><span data-stu-id="1ac31-106">The hybrid cloud and hybrid apps</span></span>

<span data-ttu-id="1ac31-107">Azure Stack zapewnia elastyczność obliczeń w chmurze w środowisku lokalnym i na krawędzi przez włączenie *chmury hybrydowej*.</span><span class="sxs-lookup"><span data-stu-id="1ac31-107">Azure Stack brings the agility of cloud computing to your on-premises environment and the edge by enabling a *hybrid cloud*.</span></span> <span data-ttu-id="1ac31-108">Azure Stack Hub, Azure Stack HCL i Azure Stack Edge rozszerzenie platformy Azure z chmury do swoich suwerennych centrów danych, biur oddziałów, pól i poza nią.</span><span class="sxs-lookup"><span data-stu-id="1ac31-108">Azure Stack Hub, Azure Stack HCI, and Azure Stack Edge extend Azure from the cloud into your sovereign datacenters, branch offices, field, and beyond.</span></span> <span data-ttu-id="1ac31-109">Dzięki temu różnorodnemu zestawowi możliwości można:</span><span class="sxs-lookup"><span data-stu-id="1ac31-109">With this diverse set of capabilities, you can:</span></span>

- <span data-ttu-id="1ac31-110">Używaj ponownie kodu i Uruchamiaj aplikacje natywne w chmurze na platformie Azure i w środowiskach lokalnych.</span><span class="sxs-lookup"><span data-stu-id="1ac31-110">Reuse code and run cloud-native apps consistently across Azure and your on-premises environments.</span></span>
- <span data-ttu-id="1ac31-111">Uruchamiaj tradycyjne Zwirtualizowane obciążenia z opcjonalnymi połączeniami z usługami platformy Azure.</span><span class="sxs-lookup"><span data-stu-id="1ac31-111">Run traditional virtualized workloads with optional connections to Azure services.</span></span>
- <span data-ttu-id="1ac31-112">Przenieś dane do chmury lub Zachowaj je w suwerennym centrum danych, aby zachować zgodność.</span><span class="sxs-lookup"><span data-stu-id="1ac31-112">Transfer data to the cloud, or keep it in your sovereign datacenter to maintain compliance.</span></span>
- <span data-ttu-id="1ac31-113">Uruchamiaj przyspieszane sprzętowo Uczenie maszynowe, kontenery lub zwirtualizowane obciążenia, a wszystko to w inteligentnej krawędzi.</span><span class="sxs-lookup"><span data-stu-id="1ac31-113">Run hardware-accelerated machine-learning, containerized, or virtualized workloads, all at the intelligent edge.</span></span>

<span data-ttu-id="1ac31-114">Aplikacje obejmujące chmury są również nazywane *aplikacjami hybrydowymi*.</span><span class="sxs-lookup"><span data-stu-id="1ac31-114">Apps that span clouds are also referred to as *hybrid apps*.</span></span> <span data-ttu-id="1ac31-115">Możesz tworzyć hybrydowe aplikacje w chmurze na platformie Azure i wdrażać je w połączonym lub rozłączonym centrum danych znajdującym się w dowolnym miejscu.</span><span class="sxs-lookup"><span data-stu-id="1ac31-115">You can build hybrid cloud apps in Azure and deploy them to your connected or disconnected datacenter located anywhere.</span></span>

<span data-ttu-id="1ac31-116">Scenariusze aplikacji hybrydowych różnią się w zależności od zasobów, które są dostępne do programowania.</span><span class="sxs-lookup"><span data-stu-id="1ac31-116">Hybrid app scenarios vary greatly with the resources that are available for development.</span></span> <span data-ttu-id="1ac31-117">Obejmują one również kwestie, takie jak Geografia, zabezpieczenia, dostęp do Internetu i inne.</span><span class="sxs-lookup"><span data-stu-id="1ac31-117">They also span considerations such as geography, security, internet access, and others.</span></span> <span data-ttu-id="1ac31-118">Chociaż opisane tutaj wzorce i rozwiązania mogą nie dotyczyć wszystkich wymagań, udostępniają wskazówki i przykłady umożliwiające eksplorowanie i ponowne użycie podczas implementowania rozwiązań hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="1ac31-118">Although the patterns and solutions described here may not address all requirements, they provide guidelines and examples to explore and reuse while implementing hybrid solutions.</span></span>

## <a name="design-patterns"></a><span data-ttu-id="1ac31-119">Wzorce projektowe</span><span class="sxs-lookup"><span data-stu-id="1ac31-119">Design patterns</span></span>

<span data-ttu-id="1ac31-120">Wzorce projektowe wycofane wskazówki dotyczące projektowania, które zostały uogólnione z rzeczywistymi scenariuszami i środowiskami klientów.</span><span class="sxs-lookup"><span data-stu-id="1ac31-120">Design patterns cull generalized repeatable design guidance, from real world customer scenarios and experiences.</span></span> <span data-ttu-id="1ac31-121">Wzorzec jest abstrakcyjny, co pozwala na zastosowanie go do różnych typów scenariuszy lub branż w pionie.</span><span class="sxs-lookup"><span data-stu-id="1ac31-121">A pattern is abstract, allowing it to be applicable to different types of scenarios or vertical industries.</span></span> <span data-ttu-id="1ac31-122">Każdy wzorzec dokumentuje kontekst i problem i zawiera omówienie przykładu rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="1ac31-122">Each pattern documents the context and problem, and provides an overview of a solution example.</span></span> <span data-ttu-id="1ac31-123">Przykładem rozwiązania jest to możliwa implementacja wzorca.</span><span class="sxs-lookup"><span data-stu-id="1ac31-123">The solution example is meant as a possible implementation of the pattern.</span></span>

<span data-ttu-id="1ac31-124">Istnieją dwa typy artykułów wzorca:</span><span class="sxs-lookup"><span data-stu-id="1ac31-124">There are two types of pattern articles:</span></span>

- <span data-ttu-id="1ac31-125">Pojedynczy wzorzec: zawiera wskazówki dotyczące projektowania dla jednego scenariusza ogólnego przeznaczenia.</span><span class="sxs-lookup"><span data-stu-id="1ac31-125">Single pattern: provides design guidance for a single general-purpose scenario.</span></span>
- <span data-ttu-id="1ac31-126">Wiele wzorców: zawiera wskazówki dotyczące projektowania, w których używane są aplikacje wielu wzorców.</span><span class="sxs-lookup"><span data-stu-id="1ac31-126">Multi-pattern: provides design guidance where the application of multiple patterns is used.</span></span> <span data-ttu-id="1ac31-127">Ten wzorzec jest często wymagany do rozwiązywania bardziej złożonych scenariuszy lub problemów specyficznych dla branż.</span><span class="sxs-lookup"><span data-stu-id="1ac31-127">This pattern is frequently required for solving more complex scenarios or industry-specific problems.</span></span>

## <a name="solution-deployment-guides"></a><span data-ttu-id="1ac31-128">Przewodnik wdrażania rozwiązania</span><span class="sxs-lookup"><span data-stu-id="1ac31-128">Solution deployment guides</span></span>

<span data-ttu-id="1ac31-129">Wskazówki krok po kroku ułatwiają wdrożenie przykładowego rozwiązania.</span><span class="sxs-lookup"><span data-stu-id="1ac31-129">Step-by-step deployment guides assist in deploying a solution example.</span></span> <span data-ttu-id="1ac31-130">Przewodnik może również odnosić się do przykładowego kodu pomocnika, który jest przechowywany w [przykładowym repozytorium rozwiązań](https://github.com/Azure-Samples/azure-intelligent-edge-patterns)usługi GitHub.</span><span class="sxs-lookup"><span data-stu-id="1ac31-130">The guide may also refer to a companion code sample, stored in the GitHub [solutions sample repo](https://github.com/Azure-Samples/azure-intelligent-edge-patterns).</span></span>

## <a name="next-steps"></a><span data-ttu-id="1ac31-131">Następne kroki</span><span class="sxs-lookup"><span data-stu-id="1ac31-131">Next steps</span></span>

- <span data-ttu-id="1ac31-132">Zapoznaj się z [rodziną Azure Stack produktów i rozwiązań](/azure-stack) , aby dowiedzieć się więcej o całym portfolio produktów i rozwiązań.</span><span class="sxs-lookup"><span data-stu-id="1ac31-132">See the [Azure Stack family of products and solutions](/azure-stack) to learn more about the entire portfolio of products and solutions.</span></span>
- <span data-ttu-id="1ac31-133">Zapoznaj się z sekcją "wzorce" i "przewodniki wdrażania rozwiązania" spisu treści, aby dowiedzieć się więcej o każdej z nich.</span><span class="sxs-lookup"><span data-stu-id="1ac31-133">Explore the "Patterns" and the "Solution deployment guides" sections of the TOC to learn more about each.</span></span>
- <span data-ttu-id="1ac31-134">Przeczytaj o [zagadnieniach dotyczących projektowania aplikacji hybrydowych](overview-app-design-considerations.md) , aby przejrzeć filary jakości oprogramowania do projektowania, wdrażania i obsługi aplikacji hybrydowych.</span><span class="sxs-lookup"><span data-stu-id="1ac31-134">Read about [Hybrid app design considerations](overview-app-design-considerations.md) to review pillars of software quality for designing, deploying, and operating hybrid apps.</span></span>
- <span data-ttu-id="1ac31-135">[Skonfiguruj środowisko programistyczne na Azure Stack](/azure-stack/user/azure-stack-dev-start.md) i [Wdróż swoją pierwszą aplikację](/azure-stack/user/azure-stack-dev-start-deploy-app.md) na Azure Stack.</span><span class="sxs-lookup"><span data-stu-id="1ac31-135">[Set up a development environment on Azure Stack](/azure-stack/user/azure-stack-dev-start.md) and [deploy your first app](/azure-stack/user/azure-stack-dev-start-deploy-app.md) on Azure Stack.</span></span>