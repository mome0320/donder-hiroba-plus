<script lang="ts">
    import { type SongScoreDetailBest } from '../../types'

    export let playdata: Promise<SongScoreDetailBest>

    const keys: Array<keyof SongScoreDetailBest> = ['good', 'pound', 'ok', 'combo', 'ng', 'hit']
</script>

{#await playdata}
로딩중...
{:then playdata}
<div class="container">
    <div class="title">
        연주 게임 베스트 스코어
    </div>
    <div class="score">
        {playdata.score}점
    </div>
    {#each keys as key}
    <div class="data">
        <img src={`image/sp/640/score_name_${key.toString()}_640.png`} alt="icon">
        {playdata[key]}회
    </div>
    {/each}
</div>
{/await}

<style>
    .container {
        display: flex;
        flex-direction: row;
        flex-wrap: wrap;

        justify-content: center;
        column-gap: 10px;
        row-gap: 3px;
    }

    .title{
        width:100%;
        text-align: center;
        font-weight: bold;
    }

    .score{
        width: 240px;
        height:35px;
        background-image: url('image/sp/640/score_back_0_640.png');
        background-size: 100% 100%;

        color:white;
        font-weight: bold;
        font-size: 18px;

        display:flex;
        align-items: center;
        justify-content: center;

        padding-top: 3px;
    }

    .data{
        width:117px;

        display:flex;
        flex-direction: row;
        justify-content: space-between;
        align-items: center;

        background-color: white;

        box-sizing: border-box;
        padding-inline: 2px;
    }

    .data > img{
        width:auto;
        height:18px;
    }
</style>
