<template>
    <div class="vc-tooltip-component">
        <vc-popover
            :show.sync="show"
            :closeable="closeable"
            :trigger="trigger"
            :effect="effect"
            :title="null"
            :content="content"
            :closeable="false"
            :placement="placement"
            :functional-show="functionalShow"
        >
            <slot></slot>
        </vc-popover>
    </div>
</template>

<style lang="less">
.vc-tooltip-component {
    display: inline-block;
    @tooltip-color: #666;

    .vc-popover-component {
        @size: 6px;
        .popover {
            padding: 0px;
            border: none;
        }
        .popover.top {
            .arrow {
                margin-bottom: -@size;
                margin-left: -@size;
                border-color: transparent; /* 覆盖掉父元素 */
                &::after {
                    border-top-color: @tooltip-color;
                }
                &::after {
                    bottom: @size;
                    border-width: @size;
                }
            }
        }
        .popover.right {
            .arrow {
                margin-top: -11 - @size / 2;
                margin-left: -@size;
                border-color: transparent; /* 覆盖掉父元素 */
                &::after {
                    border-right-color: @tooltip-color;
                }
                &::after {
                    left: @size;
                    border-width: @size;
                }
            }
        }
        .popover.bottom {
            .arrow {
                margin-top: -@size;
                margin-left: -@size;
                border-color: transparent; /* 覆盖掉父元素 */
                &::after {
                    border-bottom-color: @tooltip-color;
                }
                &::after {
                    top: @size;
                    border-width: @size;
                }
            }
        }
        .popover.left {
            .arrow {
                margin-top: -11 - @size / 2;
                margin-right: -@size;
                border-color: transparent; /* 覆盖掉父元素 */
                &::after {
                    border-left-color: @tooltip-color;
                }
                &::after {
                    right: @size;
                    border-width: @size;
                }
            }
        }
    }
    .popover-content {
        padding: 3px 10px 2px 10px;
        font-size: 12px;
        color: #fff;
        border-radius: 3px;
        background-color: @tooltip-color;
        white-space: nowrap;
    }
}
</style>

<script>
/**
 * @Tooltip Component based on vc-popover
 */

import vcPopover from 'vc-popover'

export default {
    props: {
        trigger: {
            type: String,
            default: 'hover'
        },
        effect: {
            type: String,
            default: 'vc-scale'
        },
        content: {
            type: String
        },
        placement: {
            type: String,
            default: 'right'
        },
        show: {
            type: Boolean,
            default: false
        },
        closeable: {
            type: Boolean,
            default: true 
        },
        functionalShow: {
            type: Boolean,
            default: false
        }
    },
    components: {
        vcPopover
    }
}
</script>
