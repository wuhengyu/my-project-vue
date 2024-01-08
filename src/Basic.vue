<script setup>
import { ref, computed } from "vue";
import NotFound from "./Pages/NotFound.vue";
import App from "./Pages/Basic/App.vue";
import calculate from "./Pages/Basic/calculate.vue";
import slot from "./Pages/diveComponents/slot.vue";
import BaseLayout from "./Pages/diveComponents/BaseLayout.vue";
import namedSlot from "./Pages/diveComponents/namedSlot.vue";
import ComponentModel from "./Pages/DepthComponent/ComponentModel/ComponentModel.vue";
import componentBasics from "./Pages/Basic/ComponentsBasic/oneComponent.vue";
import noBuildSteps from "./Pages/Basic/ComponentsBasic/noBuildSteps.vue";
import UseComponents from "./Pages/Basic/ComponentsBasic/UseComponents.vue";
import PassProps from "./Pages/Basic/ComponentsBasic/PassProps.vue";
import mulBlogPost from "./Pages/Basic/ComponentsBasic/mulBlogPost.vue";
import AccessTemplateReference from "./Pages/Basic/TemplateTeference/AccessTemplateReference.vue";
import BasicExample from "./Pages/Basic/Detectophone/BasicExample.vue";
import BasicUsage from "./Pages/Basic/FormInputBinding/BasicUsage.vue";
import InlineEvent from "./Pages/Basic/EventHandling/InlineEvent.vue";
import MethodEvent from "./Pages/Basic/EventHandling/MethodEvent.vue";
import VFor from "./Pages/Basic/ListRendering/VFor.vue";
import VForJs from "./Pages/Basic/ListRendering/VForJs.vue";
import VForKey from "./Pages/Basic/ListRendering/VForKey.vue";
import VForIndex from "./Pages/Basic/ListRendering/VForIndex.vue";
import VForObject from "./Pages/Basic/ListRendering/VForObject.vue";
import ConditionalRender from "./Pages/Basic/ConditionalRender/ConditionalRender.vue";
import TemplateIf from "./Pages/Basic/ConditionalRender/TemplateIf.vue";
import TemplateIfShow from "./Pages/Basic/ConditionalRender/TemplateIfShow.vue";
import Transition from "./Pages/BuiltInComponents/Transition/Transition.vue";
import TransitionCSS from "./Pages/BuiltInComponents/Transition/TransitionCSS.vue";
import TransitionCSSAnimation from "./Pages/BuiltInComponents/Transition/TransitionCSSAnimation.vue";
import TransitionCSSCustom from "./Pages/BuiltInComponents/Transition/TransitionCSSCustom.vue";
import TransitionDuration from "./Pages/BuiltInComponents/Transition/TransitionDuration.vue";
import TransitionJavaScriptHook from "./Pages/BuiltInComponents/Transition/TransitionJavaScriptHook.vue";
import TransitionReuse from "./Pages/BuiltInComponents/Transition/TransitionReuse.vue";
import EnterLeaveAnimation from "./Pages/BuiltInComponents/TransitionGroup/EnterLeaveAnimation.vue";
import ProgressiveDelayAnimation from "./Pages/BuiltInComponents/TransitionGroup/ProgressiveDelayAnimation.vue";
import KeepAliveBasicUsage from "./Pages/BuiltInComponents/KeepAlive/KeepAliveBasicUsage.vue";
import TeleportTransition from "./Pages/BuiltInComponents/Teleport/TeleportTransition.vue";
import AsyncSetup from "./Pages/BuiltInComponents/Suspense/AsyncSetup.vue";
import ParentMessage from "./Pages/DepthComponent/Props/ParentMessage.vue";
import InhertAttributesApplication from "./Pages/DepthComponent/InheritAttributes/InhertAttributesApplication.vue";
import ParentComponentInheritAttributes from "./Pages/DepthComponent/InheritAttributes/ParentComponentInheritAttributes.vue";
import TriggeringMonitorEvents from "./Pages/DepthComponent/ComponentEvent/TriggeringMonitorEvents.vue";
import EventParameters from "./Pages/DepthComponent/ComponentEvent/EventParameters.vue";
import ParentButtonClick from "./Pages/DepthComponent/ComponentEvent/ParentButtonClick.vue";
import ModelParameterParent from "./Pages/DepthComponent/ComponentModel/ModelParameterParent.vue";
import MultipleModelParent from "./Pages/DepthComponent/ComponentModel/MultipleModelParent.vue";
import ProcessModelParent from "./Pages/DepthComponent/ComponentModel/ProcessModelParent.vue";

const routes = {
  "/": App,
  "/calculate": calculate,
  "/non-existent-path": NotFound,
  "/slot": slot,
  "/namedSlot": namedSlot,
  "/BaseLayout": BaseLayout,
  "/ComponentModel": ComponentModel,
  "/componentBasics": componentBasics,
  "/noBuildSteps": noBuildSteps,
  "/UseComponents": UseComponents,
  "/PassProps": PassProps,
  "/mulBlogPost": mulBlogPost,
  "/AccessTemplateReference": AccessTemplateReference,
  "/BasicExample": BasicExample,
  "/BasicUsage": BasicUsage,
  "/InlineEvent": InlineEvent,
  "/MethodEvent": MethodEvent,
  "/VFor": VFor,
  "/VForJs": VForJs,
  "/VForKey": VForKey,
  "/VForIndex": VForIndex,
  "/VForObject": VForObject,
  "/ConditionalRender": ConditionalRender,
  "/TemplateIf": TemplateIf,
  "/TemplateIfShow": TemplateIfShow,
  "/Transition": Transition,
  "/TransitionCSS": TransitionCSS,
  "/TransitionCSSAnimation": TransitionCSSAnimation,
  "/TransitionCSSCustom": TransitionCSSCustom,
  "/TransitionDuration": TransitionDuration,
  "/TransitionJavaScriptHook": TransitionJavaScriptHook,
  "/TransitionReuse": TransitionReuse,
  "/EnterLeaveAnimation": EnterLeaveAnimation,
  "/ProgressiveDelayAnimation": ProgressiveDelayAnimation,
  "/KeepAliveBasicUsage": KeepAliveBasicUsage,
  "/TeleportTransition": TeleportTransition,
  "/AsyncSetup": AsyncSetup,
  "/ParentMessage": ParentMessage,
  "/InhertAttributesApplication": InhertAttributesApplication,
  "/ParentComponentInheritAttributes": ParentComponentInheritAttributes,
  "/TriggeringMonitorEvents": TriggeringMonitorEvents,
  "/EventParameters": EventParameters,
  "/ParentButtonClick": ParentButtonClick,
  "/ModelParameterParent": ModelParameterParent,
  "/MultipleModelParent": MultipleModelParent,
  "/ProcessModelParent": ProcessModelParent,
};
const currentPath = ref(window.location.hash);
window.addEventListener("hashchange", () => {
  currentPath.value = window.location.hash;
});
const currentView = computed(() => {
  return routes[currentPath.value.slice(1) || "/"] || NotFound;
});
</script>
<template>
  <h1>基础</h1>
  <h3>创建一个 Vue 应用</h3>
  <a href="#/Applications">Applications</a> |

  <h3>模板语法</h3>
  <a href="#/ConditionalRender">ConditionalRender</a> |
  <a href="#/TemplateIf">TemplateIf</a> |
  <a href="#/TemplateIfShow">TemplateIfShow</a> |

  <h3>响应式基础</h3>
  <a href="#/ConditionalRender">ConditionalRender</a> |
  <a href="#/TemplateIf">TemplateIf</a> |
  <a href="#/TemplateIfShow">TemplateIfShow</a> |

  <h3>计算属性</h3>
  <a href="#/ConditionalRender">ConditionalRender</a> |
  <a href="#/TemplateIf">TemplateIf</a> |
  <a href="#/TemplateIfShow">TemplateIfShow</a> |

  <h3>类与样式绑定</h3>
  <a href="#/ConditionalRender">ConditionalRender</a> |
  <a href="#/TemplateIf">TemplateIf</a> |
  <a href="#/TemplateIfShow">TemplateIfShow</a> |

  <h3>条件渲染</h3>
  <a href="#/ConditionalRender">ConditionalRender</a> |
  <a href="#/TemplateIf">TemplateIf</a> |
  <a href="#/TemplateIfShow">TemplateIfShow</a> |

  <h3>列表渲染</h3>
  <a href="#/VFor">VFor</a> | <a href="#/VForJs">VForJs</a> |
  <a href="#/VForKey">VForKey</a> | <a href="#/VForIndex">VForIndex</a> |
  <a href="#/VForObject">VForObject</a> |

  <h3>事件处理</h3>
  <a href="#/InlineEvent">InlineEvent</a> |
  <a href="#/MethodEvent">MethodEvent</a> |

  <h3>表单输入绑定</h3>
  <a href="#/InlineEvent">InlineEvent</a> |
  <a href="#/MethodEvent">MethodEvent</a> |

  <h3>生命周期</h3>
  <a href="#/InlineEvent">InlineEvent</a> |
  <a href="#/MethodEvent">MethodEvent</a> |

  <h3>侦听器</h3>
  <a href="#/InlineEvent">InlineEvent</a> |
  <a href="#/MethodEvent">MethodEvent</a> |

  <h3>模板引用</h3>
  <a href="#/InlineEvent">InlineEvent</a> |
  <a href="#/MethodEvent">MethodEvent</a> |

  <h3>组件基础</h3>
  <a href="#/InlineEvent">InlineEvent</a> |
  <a href="#/MethodEvent">MethodEvent</a> |

  <h1>逻辑复用</h1>
  <h3>组合式函数</h3>
  <h3>自定义指令</h3>
  <h3>插件</h3>

  <h1>深入组件</h1>
  <h3>注册</h3>
  <a href="#/ParentMessage">ParentMessage</a> |

  <h3>Props</h3>
  <a href="#/ParentMessage">ParentMessage</a> |

  <h3>事件</h3>
  <a href="#/TriggeringMonitorEvents">TriggeringMonitorEvents</a> |
  <a href="#/EventParameters">EventParameters</a> |
  <a href="#/ParentButtonClick">ParentButtonClick</a> |
  <a href="#/ModelParameterParent">ModelParameterParent</a> |

  <h3>组件 v-model</h3>
  <a href="#/ComponentModel">ComponentModel</a> |
  <a href="#/MultipleModelParent">MultipleModelParent</a> |
  <a href="#/ProcessModelParent">ProcessModelParent</a> |

  <h3>透传 Attributes</h3>
  <a href="#/InhertAttributesApplication">InhertAttributesApplication</a> |
  <a href="#/ParentComponentInheritAttributes"
    >ParentComponentInheritAttributes</a
  >
  |

  <h3>插槽</h3>

  <h3>依赖注入</h3>

  <h3>异步组件</h3>

  <h1>内置组件</h1>
  <h3>Transition</h3>
  <a href="#/Transition">Transition</a> |
  <a href="#/TransitionCSS">TransitionCSS</a> |
  <a href="#/TransitionCSSAnimation">TransitionCSSAnimation</a> |
  <a href="#/TransitionCSSCustom">TransitionCSSCustom</a> |
  <a href="#/TransitionDuration">TransitionDuration</a> |
  <a href="#/TransitionJavaScriptHook">TransitionJavaScriptHook</a> |
  <a href="#/TransitionReuse">TransitionReuse</a>

  <h3>TransitionGroup</h3>
  <a href="#/EnterLeaveAnimation">EnterLeaveAnimation</a> |
  <a href="#/ProgressiveDelayAnimation">ProgressiveDelayAnimation</a> |

  <h3>KeepAlive</h3>
  <a href="#/KeepAliveBasicUsage">KeepAliveBasicUsage</a> |

  <h3>Teleport</h3>
  <a href="#/TeleportTransition">TeleportTransition</a> |

  <h3>Suspense</h3>
  <a href="#/AsyncSetup">AsyncSetup</a> |

  <a href="#/App">App</a> | <a href="#/calculate">calculate</a> |
  <a href="#/non-existent-path">NotFound</a> | <a href="#/slot">slot</a> |
  <a href="#/BaseLayout">BaseLayout</a> | <a href="#/namedSlot">namedSlot</a> |
  <a href="#/componentBasics">componentBasics</a> |
  <a href="#/noBuildSteps">noBuildSteps</a> |
  <a href="#/UseComponents">UseComponents</a> |
  <a href="#/PassProps">PassProps</a> |
  <a href="#/mulBlogPost">mulBlogPost</a> |
  <a href="#/AccessTemplateReference">AccessTemplateReference</a> |
  <a href="#/BasicExample">BasicExample</a> |
  <a href="#/BasicUsage">BasicUsage</a>
  <component :is="currentView" />
</template>
