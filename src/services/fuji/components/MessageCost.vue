<template>
  <div>
    <h3 v-if="item.create_time">
      {{ $t("sensor.requestAt") }} {{ item.create_time }}
    </h3>
    <div v-if="item.status === 1" class="animation-fadein">
      <p>
        <span class="loader-ring align-vertical m-r-15"></span>
        <b class="align-vertical">1. {{ $t("sensor.cost.status1") }}</b>
      </p>
    </div>
    <div v-else-if="item.status === 2">
      <p>
        <b class="align-vertical">1. {{ $t("sensor.cost.status21") }}</b>
        <br />
        <span>{{ $t("sensor.cost.address") }}:</span>
        <br />
        <RIpfsExplorer :hash="item.liability" classStyle="align-vertical" />
        <a
          class="align-vertical i-copy m-l-10"
          href="javascript:;"
          title="copy to clipboard"
          v-clipboard:copy="item.liability"
        ></a>
      </p>
      <p>
        <span class="loader-ring align-vertical m-r-15"></span>
        <b class="align-vertical">2. {{ $t("sensor.cost.status22") }}</b>
      </p>
    </div>
    <div v-else-if="item.status === 3">
      <p>
        <b class="align-vertical">1. {{ $t("sensor.cost.status21") }}</b>
        <br />
        <span>{{ $t("sensor.cost.address") }}:</span>
        <br />
        <RIpfsExplorer :hash="item.liability" classStyle="align-vertical" />
        <a
          class="align-vertical i-copy m-l-10"
          href="javascript:;"
          title="copy to clipboard"
          v-clipboard:copy="item.liability"
        ></a>
      </p>
      <p>
        <b class="align-vertical">2. {{ $t("sensor.cost.status31") }}</b>
        <br />
        <span>{{ $t("sensor.cost.hash") }}:</span>
        <br />
        <RIpfsExplorer :hash="item.resultHash" classStyle="align-vertical" />
        <a
          class="align-vertical i-copy m-l-10"
          href="javascript:;"
          title="copy to clipboard"
          v-clipboard:copy="item.resultHash"
        ></a>
      </p>
      <p>
        <span class="loader-ring align-vertical m-r-15"></span>
        <b class="align-vertical">3. {{ $t("sensor.cost.status32") }}</b>
      </p>
      <MessageShare
        :item="item"
        :lighthouse="lighthouse"
        :model="model"
        :agent="agent"
      />
    </div>
    <div v-else-if="item.status === 4">
      <p>
        <b class="align-vertical">1. {{ $t("sensor.cost.status21") }}</b>
        <br />
        <span>{{ $t("sensor.cost.address") }}:</span>
        <br />
        <RIpfsExplorer :hash="item.liability" classStyle="align-vertical" />
        <a
          class="align-vertical i-copy m-l-10"
          href="javascript:;"
          title="copy to clipboard"
          v-clipboard:copy="item.liability"
        ></a>
      </p>
      <p>
        <b class="align-vertical">2. {{ $t("sensor.cost.status41") }}</b>
        <br />
        <span>{{ $t("sensor.cost.hash") }}:</span>
        <br />
        <RIpfsExplorer :hash="item.resultHash" classStyle="align-vertical" />
        <a
          class="align-vertical i-copy m-l-10"
          href="javascript:;"
          title="copy to clipboard"
          v-clipboard:copy="item.resultHash"
        ></a>
      </p>
      <p>
        <b class="align-vertical">3. {{ $t("sensor.cost.status42") }}</b>
        <a
          class="align-vertical i-copy m-l-10"
          href="javascript:;"
          title="copy to clipboard"
          v-clipboard:copy="JSON.stringify(item.result)"
        ></a>
        <br />
        <code>
          <pre>{{ item.result }}</pre>
        </code>
      </p>
      <MessageShare
        :item="item"
        :lighthouse="lighthouse"
        :model="model"
        :agent="agent"
      />
    </div>
  </div>
</template>

<script>
import MessageShare from "./MessageShare";

export default {
  props: ["item", "lighthouse", "model", "agent"],
  components: { MessageShare }
};
</script>
