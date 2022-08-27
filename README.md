// 更新奖励的情况
    function updateReward() private  {
        uint256 GuessBettorNums = (guessListMap[hgmGlobalId]).length;
        for(uint256 i = 0; i < GuessBettorNums; i++) {
            GuessBettor storage gb = guessListMap[hgmGlobalId][i];
            WinningResult memory wr = WinningMap[hgmGlobalId];
            if (gb.betType == uint256(BettorType.Big) && (wr.sumResult >= 14 && wr.sumResult <= 27)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(195).div(100);
                gb.reWardVale = _reWardVale; // 1.95
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.Small) && (wr.sumResult >= 0 && wr.sumResult <= 13)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(195).div(100);
                gb.reWardVale = _reWardVale; // 1.95
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.Single) && wr.sumResult % 2 == 1) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(195).div(100);
                gb.reWardVale = _reWardVale; // 1.95
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.Double) && wr.sumResult % 2 == 0) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(195).div(100);
                gb.reWardVale = _reWardVale; // 1.95
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.SmallSingle) && wr.sumResult % 2 == 1 && (wr.sumResult >= 0 && wr.sumResult <= 13)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(195).div(100);
                gb.reWardVale = _reWardVale; // 4.87
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.SmallDouble) && wr.sumResult % 2 == 0 && (wr.sumResult >= 0 && wr.sumResult <= 13)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(325).div(100);
                gb.reWardVale = _reWardVale; // 3.25
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.BigSingle) && wr.sumResult % 2 == 1 && (wr.sumResult >= 14 && wr.sumResult <= 27)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(325).div(100); // 3.25;
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.BigDouble)  && wr.sumResult % 2 == 0 && (wr.sumResult >= 14 && wr.sumResult <= 27)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(487).div(100);
                gb.reWardVale = _reWardVale; // 4.87
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.Dragon) && wr.numberList[0] > wr.numberList[2]) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(200).div(100); // 2
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.Tiger) && wr.numberList[0] < wr.numberList[2]) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(200).div(100); // 2
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.Combine) && wr.numberList[0] == wr.numberList[2]) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(800).div(100); // 8
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.BaccaratBanker) && wr.bankerNumber > wr.idleNumber) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(200).div(100); // 2
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.BaccaratIdle) && wr.bankerNumber < wr.idleNumber) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(200).div(100); // 2
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.BaccaratSame)  && wr.bankerNumber == wr.idleNumber) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(800).div(100); // 8
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.NiuNiu_zhuang)  && niuniuZhuangWin(wr.bankerNumber, wr.idleNumber)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(getNiuNiuScale(wr.bankerNumber, wr.idleNumber));
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.NiuNiu_xian)  && !niuniuZhuangWin(wr.bankerNumber, wr.idleNumber)) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(getNiuNiuScale(wr.bankerNumber, wr.idleNumber));
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }

            if (gb.betType == uint256(BettorType.SinglePoint_0) || gb.betType == uint256(BettorType.SinglePoint_27)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(999); // 999
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_1) || gb.betType == uint256(BettorType.SinglePoint_26)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(333); // 999
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.SinglePoint_2) || gb.betType == uint256(BettorType.SinglePoint_25)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(167); // 167
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_3) || gb.betType == uint256(BettorType.SinglePoint_24)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(100); // 100
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_4) || gb.betType == uint256(BettorType.SinglePoint_23)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(66); // 66
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_5) || gb.betType == uint256(BettorType.SinglePoint_22)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(47); // 47
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_6) || gb.betType == uint256(BettorType.SinglePoint_21)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(35); // 35
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_7) || gb.betType == uint256(BettorType.SinglePoint_20)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(28); // 28
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_8) || gb.betType == uint256(BettorType.SinglePoint_19)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(22); // 22
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_9) || gb.betType == uint256(BettorType.SinglePoint_18)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(18); // 18
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_10) || gb.betType == uint256(BettorType.SinglePoint_17)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(16); // 16
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
            if (gb.betType == uint256(BettorType.SinglePoint_11) || gb.betType == uint256(BettorType.SinglePoint_16)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(15); // 15
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_12) || gb.betType == uint256(BettorType.SinglePoint_15)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(14); // 14
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
             if (gb.betType == uint256(BettorType.SinglePoint_13) || gb.betType == uint256(BettorType.SinglePoint_14)) && (wr.sumResult == gb.PiointNum) {
                gb.isReward = true;
                uint256 _reWardVale = gb.value.mul(40).div(3); // 13.333
                gb.reWardVale = _reWardVale;
                updateRewardLists(gb.account, gb.hgmId, gb.index, _reWardVale);
                continue;
            }
        }
    }

// 投注
    function createBettor(uint256 amount, uint256 betType) public returns (bool) {
        // 检查投注类别是否正确
        require(_betType >= uint256(BettorType.Big) && _betType <= uint256(BettorType.BaccaratSame), "createBettor: invalid bettor type, please bette repeat");
        // 最少投资金额 10U
        require(_amount >= 10000000, "createBettor: bette amount must more than 10U");
        // 检查投注者的余额是否足够
        require(betteToken.balanceOf(msg.sender) >= _amount, "createBettor: bettor account balance not enough");

        if (block.number > endBlock) {
            //结束当前期游戏
            endHashGame();
        }
        GuessBettor memory gb = GuessBettor({
            account: msg.sender,
            index: (usersGuessListMap[msg.sender][hgmGlobalId]).length,
            value: _amount,
            hgmId: hgmGlobalId,
            betType: _betType,
            isReward: false,
            PiointNum: _betType - 16,
            reWardVale: 0
        });
        //玩家历史记录
        guessListMap[hgmGlobalId].push(gb);
        //玩家信息列表
        userInfo storage user = userInfoList[msg.sender];
        user.totalBetted = user.totalBetted + _amount;
        //玩家下注记录
        usersGuessListMap[msg.sender][hgmGlobalId].push(gb);
        //当期下注总额
        WinningResult storage currentWinningResult = WinningMap[hgmGlobalId];
        currentWinningResult.totalBetted = currentWinningResult.totalBetted + _amount;
        emit GuessBettorCreate(msg.sender, amount, betType, hgmGlobalId, gb.index);
        require(betteToken.transferFrom(msg.sender, address(this), _amount));
        return true;
    }