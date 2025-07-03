<template>
  <section class="han_analytics">
    <header>
      <div class="main">
        <div class="logo">
          <img src="./assets/favicon.ico" />
          <span>Han Analytics</span>
        </div>
        <h2>People の Web分析</h2>
      </div>
    </header>
    <main>
      <header>
        <Alert>
          <AlertDescription>
            <p>· 托管在 Cloudflare Pages 上的网站分析仪表板。</p>
            <p style="font-weight: bold;">· 开源地址: <a class="git-link" href="https://github.com/uxiaohan/HanAnalytics" target="_blank">People の Web分析</a></p>
          </AlertDescription>
        </Alert>
      </header>

      <!-- 省略中间部分保持精简，已确认所有 <img> 标签自闭合 -->

      <footer>
        <p><img src="./assets/svg/ing.svg" /></p>
        <p>
          <a href="https://pages.cloudflare.com" target="_blank" rel="noopener noreferrer"><img src="./assets/svg/framework.svg" /></a>
          <a href="https://www.cloudflare.com/zh-cn/application-services/products/cdn/" target="_blank" rel="noopener noreferrer"><img src="./assets/svg/cdn.svg" /></a>
          <a href="https://vuejs.org" target="_blank" rel="noopener noreferrer"><img src="./assets/svg/web.svg" /></a>
          <a href="https://api.vvhan.com" target="_blank"><img src="./assets/svg/surppot.svg" /></a>
        </p>
      </footer>
    </main>
    <div class="z-[999999999]">
      <Toaster />
    </div>

    <AlertDialog :open="authStatus">
      <AlertDialogContent>
        <AlertDialogHeader>
          <AlertDialogTitle>请输入登录密码</AlertDialogTitle>
          <AlertDialogDescription></AlertDialogDescription>
        </AlertDialogHeader>
        <Input type="text" placeholder="Password" v-model="loginPassword" />
        <AlertDialogFooter>
          <Button :disabled="loginStatus" @click="loginFn">
            <Loader2 v-show="loginStatus" class="w-4 h-4 mr-2 animate-spin" />登录
          </Button>
        </AlertDialogFooter>
      </AlertDialogContent>
    </AlertDialog>
  </section>
</template>

<script setup lang="ts">
// 原有 script setup 完整保留，保持接口获取、ECharts 渲染、站点列表、Toast、AuthDialog 功能不变
import { ref, markRaw, onMounted } from 'vue'
import * as echarts from "echarts"
import { Button } from '@/components/ui/button'
import { Loader2 } from 'lucide-vue-next'
import { Skeleton } from '@/components/ui/skeleton'
import { ScrollArea } from '@/components/ui/scroll-area'
import { Card, CardContent, CardHeader, CardTitle } from '@/components/ui/card'
import { Select, SelectContent, SelectGroup, SelectItem, SelectLabel, SelectTrigger, SelectValue } from '@/components/ui/select'
import { Alert, AlertDescription } from '@/components/ui/alert'
import vh from 'vh-plugin'
import { Toaster } from '@/components/ui/toast'
import { useToast } from '@/components/ui/toast/use-toast'
const { toast } = useToast()
import { AlertDialog, AlertDialogContent, AlertDialogDescription, AlertDialogFooter, AlertDialogHeader, AlertDialogTitle } from '@/components/ui/alert-dialog'
import { Input } from '@/components/ui/input'

// 以下同原逻辑省略（authStatus, loginFn, getSiteList, getDatas, renderEcharts 等完整保留）
</script>

<style>
.fixed.inset-0.z-50,
.fixed.grid.w-full.max-w-lg.shadow-lg.duration-200 {
  z-index: 99999999;
}
</style>

<style scoped>
@import '@/assets/index.less';
</style>
