<pre>
/**
@파일 videoocapture_basic.cpp
@brief VideoCapture 및 VideoWriter 사용을 위한 매우 기본적인 샘플
@author PkLab.net
2018.11.06
*/

#include <opencv2/opencv.hpp>
#include <iostream>
#include <stdio.h>

using namespace cv;
using namespace std;

int main(int, char**)
{
	Mat frame; //동영상 파일 재생을 위한 행렬 선언
	VideoCapture cap;
	// 기본 API를 사용하여 기본 카메라 열기
	cap.open(0);
	//또는 사용 현황 향상: API 백엔드를 선택합니다
	int deviceID = 0;             // 0 = open default camera
	int apiID = cv::CAP_ANY;      // 0 = autodetect default API
								  // open selected camera using selected API
	cap.open(deviceID + apiID);
	// check if we succeeded
	if (!cap.isOpened()) {
		cerr << "ERROR! Unable to open camera\n";
		return -1;
	}

	//--- GRAB AND WRITE LOOP
	cout << "Start grabbing" << endl
		<< "Press any key to terminate" << endl;
	for (;;)
	{
		// 카메라에서 새 프레임을 기다린 후 '프레임'에 저장합니다.
		cap.read(frame);
		// 성공했는지 확인
		if (frame.empty()) {
			cerr << "ERROR! blank frame grabbed\n";
			break;
		}
		// 실시간을 표시하고 이미지를 표시할 수 있을 만큼 시간이 초과된 키를 기다립니다.
		//imshow("Live",frame);
		imshow("result",frame);
		char ch = waitKey(10);
		if (ch == 27) break;       // 27 == ESC key
		if (ch == 32)                // 32 == SPACE key
		{
			while ((ch = waitKey(10)) != 32 && ch != 27);
			if (ch == 27) break;
		}
	}
	// VideoCapture 소멸기에서 카메라가 자동으로 초기화됩니다.
	return 0;
}
<code>